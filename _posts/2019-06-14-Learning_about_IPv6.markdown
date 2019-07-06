---
layout: post
title:  "Learning about IPv6 and its cool"
date:   2019-06-14 01:02:03 -0700
---
I see the end of the CCENT(ICND1) course so I must be close. Trying to get a good understanding of IPv6 since I think it would be good to use in the future.

IPv6 SLAAC (State Less Auto Address Configuration) is cool because you don’t have to setup a DHCP Server or setup static IPs to have basic device connectivity. However, DHCPv6 Servers are still needed for other resources. 

An example where I have used it is if you are setting up a quick virtual machine to test something out. You can connect to it with IPv6 instead of having to manually configure IPs or spend time setting up a DHCP server for something that is just a quick test on a laptop.

Another example that I can see being extremely useful would be to use a globally unique ipv6 address on a router’s interface. That way when you are switching ISP (Internet Service Providers) remotely on your box. You won’t lose access as long as the ISP passes IPv6.  It seems extremely useful if you are setting up redundant routers as well since you wouldn’t need to pay for a minimum of 3 public IPs for every setup.

