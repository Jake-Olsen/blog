---
layout: post
title:  "Packet Limiter Weirdness in pfSense"
date:   2021-10-31 01:02:03 -0700
---

Putting packets in a queue then timing when they should go out based off of a priority algorithm can help maintain consistency. This helps out more when a network tends to struggle getting bandwidth. As when a Queue in the gateway builds up it can create what is called Bufferbloat where there is so many things in the buffer it can slow down packets that have more urgency to get out. Such as Video, Voice Calls, and Online Gaming.

I have a Gigabit connection at home so I don't need to worry that much about setting up a Packet Queue since its very close to a 1:1 pipe. However I still want to prioritize my voice traffic and online gaming traffic. When I setup the packet queue in PfSense with recommended limiters and other settings I get very strange traceroute results.
Looks lke other people have reported this issue in forums and in pfsense's bug tracker.
<https://redmine.pfsense.org/issues/9263>

I had a suspicion recently that maybe it was somehow hardware related. So I decided to run some tests to see.

So to start with I'm running a traceroute from a virtual machine that is behind my Netgate 1100 pfSense+ that is behind the Generic i5 Fanless PC also running pfSense which then goes through NAT to the Internet. So the lab is behind double NAT.

Test 1: No QoS, Double NAT.
	{% highlight console %}
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
 1  pfSense.localdomain (10.6.0.1)  0.702 ms  0.636 ms  0.620 ms
 2  192.168.6.1 (192.168.6.1)  1.145 ms  1.070 ms  1.045 ms
 3  REDACTED (REDACTED)  1.830 ms  2.272 ms  2.619 ms
 4  10.1.0.2 (10.1.0.2)  11.728 ms  11.934 ms  11.907 ms
 5  7-1-10.bear1.Sacramento1.Level3.net (4.53.202.29)  12.124 ms  12.241 ms  12.218 ms
 6  * * *
 7  4.7.18.106 (4.7.18.106)  15.840 ms  21.234 ms  21.178 ms
 8  one.one.one.one (1.1.1.1)  15.546 ms  15.536 ms  15.509 ms
{% endhighlight%}

Test 2: QoS on Upstream Router, No QoS on Netgate 1100, Double NAT.
{% highlight console %}
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
 1  pfSense.localdomain (10.6.0.1)  0.660 ms  0.629 ms  0.609 ms
 2  192.168.6.1 (192.168.6.1)  1.128 ms  2.597 ms  2.617 ms
 3  one.one.one.one (1.1.1.1)  4.911 ms  4.875 ms  4.871 ms
 4  one.one.one.one (1.1.1.1)  13.391 ms  13.375 ms  13.097 ms
 5  one.one.one.one (1.1.1.1)  13.665 ms  13.521 ms  13.497 ms
 6  * * *
 7  one.one.one.one (1.1.1.1)  15.936 ms  19.188 ms  19.068 ms
 8  one.one.one.one (1.1.1.1)  15.112 ms  15.134 ms  15.080 ms
{% endhighlight%}

Test 3: No QoS on Upstream, QoS on Netgate 1100, Double NAT
	{% highlight console %}
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
 1  pfSense.localdomain (10.6.0.1)  0.727 ms  10.776 ms  10.742 ms
 2  one.one.one.one (1.1.1.1)  21.100 ms  21.177 ms  21.153 ms
 3  one.one.one.one (1.1.1.1)  21.514 ms  21.199 ms  21.494 ms
 4  one.one.one.one (1.1.1.1)  21.722 ms  21.706 ms  21.738 ms
 5  one.one.one.one (1.1.1.1)  22.251 ms  22.219 ms  22.265 ms
 6  one.one.one.one (1.1.1.1)  25.033 ms  23.567 ms  23.381 ms
 7  one.one.one.one (1.1.1.1)  31.227 ms  21.366 ms  20.017 ms
 8  one.one.one.one (1.1.1.1)  15.158 ms  15.124 ms  15.478 ms
{% endhighlight%}

On Test 3 where QoS is on. You can see the ping latency is nearly double which is terrible. I feel like I'm doing something wrong with this setup, but I was just following pfsense's guidelines on the setup so I'm not sure.

QoS ON
	{% highlight console %}
jake@Debian10B:~$ ping 1.1.1.1                             
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.               
64 bytes from 1.1.1.1: icmp_seq=1 ttl=57 time=35.5 ms      
64 bytes from 1.1.1.1: icmp_seq=2 ttl=57 time=35.1 ms      
64 bytes from 1.1.1.1: icmp_seq=3 ttl=57 time=35.1 ms      
^C                                                         
--- 1.1.1.1 ping statistics ---                            
3 packets transmitted, 3 received, 0% packet loss, time 5ms
rtt min/avg/max/mdev = 35.068/35.232/35.505/0.194 ms  
{% endhighlight%}      

QoS OFF
	{% highlight console %}
jake@Debian10B:~$ ping 1.1.1.1                             
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.               
64 bytes from 1.1.1.1: icmp_seq=1 ttl=57 time=16.2 ms      
64 bytes from 1.1.1.1: icmp_seq=2 ttl=57 time=15.7 ms      
64 bytes from 1.1.1.1: icmp_seq=3 ttl=57 time=15.7 ms      
^C                                                         
--- 1.1.1.1 ping statistics ---                            
3 packets transmitted, 3 received, 0% packet loss, time 5ms
rtt min/avg/max/mdev = 15.674/15.855/16.165/0.220 ms       
{% endhighlight%}                                         


Disabling the Queue but keeping just the floating rule and limiter still shows the weird traceroute, but without the double latency.

	{% highlight console %}
jake@Debian10B:~$ traceroute 1.1.1.1
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
1  pfSense.localdomain (10.6.0.1)  0.408 ms  0.374 ms  0.369 ms
2  one.one.one.one (1.1.1.1)  1.188 ms  1.165 ms  1.207 ms
3  one.one.one.one (1.1.1.1)  1.854 ms  2.686 ms  2.360 ms
4  one.one.one.one (1.1.1.1)  11.744 ms  11.873 ms  11.838 ms
5  one.one.one.one (1.1.1.1)  12.199 ms  12.327 ms  12.131 ms
6  one.one.one.one (1.1.1.1)  14.610 ms  14.343 ms  14.175 ms
7  one.one.one.one (1.1.1.1)  15.480 ms  15.748 ms  15.870 ms
8  one.one.one.one (1.1.1.1)  15.074 ms  15.200 ms  15.189 ms
{% endhighlight%}

Disabling the limiters
	{% highlight console %} 
jake@Debian10B:~$ traceroute 1.1.1.1
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
1  pfSense.localdomain (10.6.0.1)  0.768 ms  0.727 ms  0.716 ms
2  192.168.6.1 (192.168.6.1)  1.221 ms  1.199 ms  1.299 ms
3  REDACTED  3.043 ms  1.976 ms  2.342 ms
4  10.1.0.2 (10.1.0.2)  11.875 ms  12.098 ms  12.082 ms
5  7-1-10.bear1.Sacramento1.Level3.net (4.53.202.29)  12.232 ms  12.311 ms  12.302 ms
6  ae-2-3611.ear4.SanJose1.Level3.net (4.69.211.221)  14.996 ms  14.444 ms  14.390 ms
7  4.7.18.106 (4.7.18.106)  21.979 ms  21.964 ms  21.940 ms
8  one.one.one.one (1.1.1.1)  15.232 ms  15.253 ms  15.214 ms
{% endhighlight%}

Finally found a way to enable a Queue but without the weird traceroute results / double latency. It looks like the pfSense limiter is what causes it. Doesn't matter if you are on your own hardware or netgate hardware.

Add in a basic interface traffic shaper and no more weird issues, but you still get to use the easy codel.

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\pfQ-1.webp" 
		alt="X"
	>
</picture>

Went from 16ms to 13ms in a simple estimate on speedtest.net; however, your mileage may vary.
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\pfQ-2.webp" 
		alt="X"
	>
</picture>
