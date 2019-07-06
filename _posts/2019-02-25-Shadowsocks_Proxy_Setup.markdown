---
layout: post
title:  "Shadowsocks Proxy"
date:   2019-02-25 01:02:03 -0700
---
There hasn't been much progress has been made with the blog. However, I am still studying for the CCNA.

Thought I would write up a post for how I got the Shadow Socks Server online.
I thought I would try some automated setup scripts that were posted online to speed up the process of getting it setup, however none of them worked. Even installing the exact same Linux distro version that was mentioned in the guide. Time to jump in and do it manually. I set it up on Ubuntu since that was a few different tutorials were using. That way I could get a hang of a newer version of shadowsocks.

Here are the tutorials that I found that got the basics up and running:
https://www.jumpthegreatfirewall.com/shadowsocks/ (Missing a couple steps, but it mostly got it)

https://github.com/shadowsocks/shadowsocks/issues/646 (Found the solution to an error I was getting, just had to install an update)

https://shadowsocks.org/en/config/quick-guide.html (A handy QR Code Generator to quickly get your custom setup working on your phone)

During the process when I wasn't seeing the results I wanted to. I used TCP Dump on the WAN port of my Ubiquiti router's command line to see if the traffic from my phone's mobile data was at least getting to my router.
Though I don't know my Public IPv4 for mobile data since it gets converted from IPv6 to IPv4. I just filtered out the default port while initially setting it up, and you can see that I was receiving a request for port 8000. 

{% highlight console %}
user@ubnt:~$ sudo tcpdump -n -i eth0 | grep 8000
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
19:08:42.216473 IP MOBILE_DATA_IP.32.41760 > WAN_HOME_IP.24.8000: UDP, length 51
19:08:42.216482 IP MOBILE_DATA_IP.32.46744 > WAN_HOME_IP.24.8000: UDP, length 51
19:08:42.216876 IP MOBILE_DATA_IP.32.54093 > WAN_HOME_IP.24.8000: UDP, length 52
19:08:42.416714 IP MOBILE_DATA_IP.32.58389 > WAN_HOME_IP.24.8000: UDP, length 71
19:08:45.218682 IP MOBILE_DATA_IP.32.41760 > WAN_HOME_IP.24.8000: UDP, length 51
19:08:45.226359 IP MOBILE_DATA_IP.32.46744 > WAN_HOME_IP.24.8000: UDP, length 51
{% endhighlight %}

However something still isn't right, so lets check by running Wireshark on the virtual ethernet port and filter for the Hyper-V Virtual Machine's IP.   
{% highlight text %}ip.addr == 10.3.72.171 {% endhighlight %}

I wasn't receiving any data past the firewalls so after some more tinkering I got the port forward to work correctly. I can now see the data.

Oddly enough the Shadowsocks VPN App on android failed the 'test', but I was able to connect to the proxy and browse the web and the correct public IP was showing up now. So it is working even though the app's built-in test fails.

The next thing I wanted to do was to change the port from the default 8000 to 443 so that way it would look like normal HTTPS Traffic to any peering eyes.
Which is pretty easy to do. Change the config file, restart the Shadowsocks Service, and open up port 443. Then update the port forward on the router.
