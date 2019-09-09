---
layout: post
title:  "Combining VMs (VPN, Proxy, SSH)"
date:   2019-03-17 09:00:11 -0700
---
I decided to combine my VMs (Virtual Machines) into a single VM because having 3 servers running all the time eats up a bit of my RAM and processing on my Gaming PC.

The 3 that are running 24x7 are:  
1) A VM running Debian 9 that has SSH open to the internet but is restricted with a Public Key.  
2) The OpenVPN Server running Debian 9  
3) The Shadowsock Proxy Server running Ubuntu 16.04.2

I should be able to combine all 3 into a single server, which should help because then I'll only be running 1 OS instead of 3, so the backgrounds tasks won't be duplicated. We'll see if I can squeeze some time into getting them setup before the weekend is over.

The first way I had initially setup OpenVPN stemmed from this [Hak5 video on YouTube]. It is great for manually setting it up because it helps you understand how it works and how to troubleshoot it.

I wanted to try to automate the setup to save time. I was messing around learning how bash worked and got most of it working, but there were some parts that were not reliably repeatable for some reason. I set it aside a while ago to work on my CCNA. I did however want to try out a script that I found on GitHub to help speed up remaking my OpenVPN Server. Looking through it [github.com/angristan/openvpn-install] I didn't see anything malicious or any other servers it would point to, so it appears to be safe. ~~It worked just fine on my Ubuntu 16.04.2 VM.~~

I was able to finish the setup this weekend.  Not too complicated since I already setup a Shadowsocks server, the OpenVPN Script worked, and SSH Public Private key setup is really simple too.


[Hak5 video on YouTube]: https://youtu.be/XcsQdtsCS1U

[github.com/angristan/openvpn-install]: https://github.com/angristan/openvpn-install

**August 2019 Update: My Ubuntu Machine had many complications and couldn't maintain a reliable network connection. I deleted the Ubuntu Server VM and I'll eventually remake it on Debian since I didn't have stability problems in the past with it.**
