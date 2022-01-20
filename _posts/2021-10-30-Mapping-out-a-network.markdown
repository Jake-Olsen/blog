---
layout: post
title:  "Mapping out a network"
date:   2021-10-30 01:02:03 -0700
---

I may move part of this into a separate guide section if I create more guide like posts. This is a very rough draft, so it is not very cohesive. Version 2 I would organize it more along with creating an actual visual map to show each section then a final map with everything connected.

I am aware that some other vendors have automatic visual map. I just have not worked with them outside of a Unifi switch that I have at home currently. They also don't seem to be fully reliably. For example:

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\HowMapNetPic-1.webp" 
		alt="X"
	>
</picture>

In this automatically generated chart  it shows the Unifi Wireless AP's Port 1 connects back to the Unifi Switch on Port 16. However if you look at Laptop C930 it also shows it is on port 16. Which it does lead back to that port, but it actually connects through Port 2 on the Unifi AP in the other room. In the new Unifi network topology it also looks like the  Flex Mini switch is online when it hasn't been powered on for over a year.

In the older Unifi interface it correctly doesn't show at all in the topology view. Though with testing it also doesn't show the laptop plugged into the Wireless AP Port 2 just shows port 16.

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\HowMapNetPic-2.webp" 
		alt="X"
	>
</picture>

Note: most of these commands are for Cisco , however the general idea still applies with other vendor equipment.
    For example :(Cisco show mac address table, Allied Telesis/Dell : show bridge address table)

Example Devices:
{% highlight console %}
Router: 	fc:d4:f2:aa:bb:c1
Root Switch:	24:16:9d:aa:bb:23
Switch 1: 	24:16:9d:aa:bb:11
Switch 2: 	24:16:9d:aa:bb:47
Switch 3: 	24:16:9d:aa:bb:33
Switch 4: 	24:16:9d:aa:bb:59
{% endhighlight%}

First find the root switch that is connected to the Router.
In this case I'll use a Linux computer as the example as I usually work on Linux routers at work.
ip addr list eth0
You should see similar to this:

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\HowMapNetPic-3.webp" 
		alt="X"
	>
</picture> 

Grab the MAC Address (Example MAC: fc:d4:f2:aa:bb:c1)
 
Then go to the switch that you think is the core. If you have no idea, then just check every switch you discover until you find it.
show mac address-table address fc:d4:f2:aa:bb:c1
Verify the port is correct
show mac address-table interface <PORT HERE>
Then make that switch the spanning tree root if it isn't already
Spanning tree priority 0
 
Note down all your switches that you think have. Switch 1, Switch 2, Switch 3, ect.

Now to do some shortcuts if possible:
If LLDP is enabled you can find other devices that also use LLDP. It will sometimes even show the hostname/mac of the device 
	{% highlight console %}
Show lldp neighbors
{% endhighlight%}
	{% highlight console %}

Switch4# show lldp neighbors

 Port       Device ID          Port ID      	System Name    
------- ----------------- -----------------	-------------------
1/e6    24:16:9d:aa:bb:23     gi1/1/26		Root Switch

1/e9    64:16:00:00:00:01       gi1		Polycom  

{% endhighlight%}
Note: This won't work on older Cisco devices as they didn't support LLDP.
If CDP is enabled you can also note those quick too. (Mostly Cisco Only Devices)
	{% highlight console %}
Show cdp neighbors
{% endhighlight%}
	{% highlight console %}
SW3#show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone

Device ID        Local Intrfce     Holdtme    Capability  Platform  Port ID
50000000000006		Fas 0/24       	162        	S I      	SG300-10P gi10
SEP4CBC48000001  	Fas 0/24       	142        	H P      	IP Phone  Port 1
Switch-11    		Fas 0/24       	150        	S I      	WS-C3550- Fas 0/24
Switch-22    		Fas 0/24       	151        	S I      	WS-C3550- Fas 0/24
Root_Switch    		Fas 0/24       	168        	S I      	SG350X-48P gi10
{% endhighlight%}



Show spanning tree is how you can find the other switches that are running spanning tree (STP). Which most switches should all be using STP on the ports.
To make sure spanning tree is enabled on all ports run:
	{% highlight console %}
show spanning-tree
{% endhighlight%}
You should see similar to this on the core of the network:
	{% highlight console %}
Root_Switch# show spanning-tree


Spanning tree enabled mode RSTP
Default port cost method:  short



  Root ID    Priority    0
             Address     24:16:9d:aa:bb:23
             This switch is the root
             Hello Time  2 sec  Max Age 20 sec  Forward Delay 15 sec

  Number of topology changes 64 last change occurred 651:28:23 ago
  Times:  hold 1, topology change 35, notification 2
          hello 2, max age 20, forward delay 15

Interfaces
 Name   State   Prio.Nbr   Cost     Sts   Role PortFast       Type
------ -------- -------- --------- ------ ---- -------- -----------------
 1/e1  enabled   128.1      19      Frw   Desg    No       P2P (RSTP)
 1/e2  enabled   128.2      19      Frw   Desg    No       P2P (RSTP)
{% endhighlight%}

On the switches that aren't root you'll see what port is determined as the best path to the root switch.

	{% highlight console %}
show spanning tree detail
{% endhighlight%}
 
	{% highlight console %}
Look for details such as:
Root port is 24 (FastEthernet0/24)"
Designated root........24:16:9d:aa:bb:23
Designated bridge......24:16:9d:aa:bb:33 <ROOT or OTHER MAC HERE>
Designated port id is 128.XX
{% endhighlight%}

If the designated bridge address doesn't match the root mac, then there is another switch in-between it and the root.
The Port ID is the port of the switch that it connects directly to.
For example if you have switches connected like this:
	{% highlight console %}
Root_Switch port 1 > Switch_1 port 23 > SW7 port 48
Root will be Root Switch's Address 24:16:9d:aa:bb:23
SW7 Designated bridge will be SW1
SW7 Designated port id should show 128.23
If you also had
SW CORE A Port 3 > SW2 port 22 > SW6 port 47
Root will be Switch A
SW2 Designated bridge will be Root
SW2 Designated port will be 128.3
SW6 Designated bridge will be SW2
SW6 Designated port will be 128.22
{% endhighlight%}

For example: 
	{% highlight console %}
Switch7# show spanning-tree

Root ID    Priority    0
           Address     24:16:9d:aa:bb:23
           Cost        19
           Port        24 (FastEthernet0/24)
           Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec

Bridge ID  Priority    32769  (priority 32768)
           Address     24:16:9d:aa:bb:11
           Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec
           Aging Time 300
{% endhighlight%}

You can see how 7's next bridge is Switch 1's address.
Which is the path it will take to get to the root switch address.



Note: Ports that go beyond 48 may be higher speed ports(Such as Gigabit or 10 Gigabit) or ports of a stacked switch
	{% highlight console %}
1/g1  enabled   128.49
1/g2  enabled   128.50
1/g3  enabled   128.51
1/g4  enabled   128.52
2/e1  enabled   128.53
2/e2  enabled   128.54
{% endhighlight%}

Further beyond those steps if STP is not enabled.
Looking by mac address is the one of the last few options.
	{% highlight console %}
show mac address-table address <MAC HERE>
{% endhighlight%}
Verify the port is correct
	{% highlight console %}
show mac address-table interface <PORT HERE>
{% endhighlight%}
