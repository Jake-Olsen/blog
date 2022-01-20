---
layout: post
title:  "UPnP 169 Weirdness and Terminals"
date:   2020-06-11 01:02:03 -0700
---

I don't recommend setting up npcap or wireshark on a gaming pc. I figured out something weird. Apparently the reason why my games haven't been working that well on the new router is because. The Games have been trying to use upnp to open a port to the npcap loopback adapter that I have for Wireshark/Nmap. Secure mode prevents a device from setting up ports for another device on the network. so I disabled secure mode and for some reason some games on my desktop 192.x.x.73 was trying to setup a port for 169.254.x.x and being blocked. Yes I know UPnP isn't secure in a workplace environment but this is my home gaming environment so it's fine. I'll accept that risk for the convenience of having my games work.

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\upnpWT-1.webp" 
		alt="UPnP Weirdness Screenshot"
	>
</picture>

Removing the npcap and wireshark drivers have fixed that problem. I'll probably just monitor network traffic with another computer like my laptop when I need to.  

Another interesting issue with CloudFlare's DNS Malware Blocking (1.1.1.2) is that it blocks putty downloads? If you query 1.1.1.2 with dig using WSL 2 dns utils it doesn't block it and caches it so you can still get to it?  

KiTTY doesn't allow you to use tmux commands. Because it uses the Ctrl+B and arrow keys to adjusts brightness? I guess the first try was enough for me to not use it again. KiTTY does support port knocking. However I think I'll try out port knocking on a server eventually. I just don't have a need for it since everything is internal at the moment I don't have anything open on the firewall besides the Game servers. Port knocking seems like a really secure and interesting concept. Though a VPN would still probably be better. Maybe a combination of a VPN & Port Knocking once you get inside. Perhaps Port Knocking to connect to the VPN might be possible?

Found out that a Terminal can make remote systems look better.    
For example this is a comparison of the XCP-NG console:
 
PuTTY terminal
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\upnpWT-2.webp" 
		alt="PuTTY Terminal Screenshot"
	>
</picture>

Linux terminal
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\upnpWT-3.webp" 
		alt="Linux Terminal Screenshot"
	>
</picture>

Windows Powershell
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\upnpWT-4.webp" 
		alt="Powershell Terminal Screenshot"
	>
</picture>

I'll probably drop PuTTY soon. I just wanted to use WinSSHTerm during my setup while I'm still sick to make it easier. As it can tie in your passwords, SSH keys, IPs, WinSCP for moving files and more. I also got used to it while I was doing my cisco labs last year.
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\upnpWT-5.webp" 
		alt="WinSSHTerm Screenshot"
	>
</picture>

I haven't been keeping up with all my blog posts. However GitHub does have a cool automatic security alert system. So I've been applying those patches to the website when I get the email alerts from them. The first time I manually fixed the code myself, however a colleague explained a bit better how git worked so now I'm just applying the recommended patches that the system auto writes.  Most of them have just been version increases as part of the Jekyll/Ruby Gems and they haven't broken any part of the site/template yet. 
