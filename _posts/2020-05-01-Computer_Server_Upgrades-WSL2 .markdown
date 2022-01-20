---
layout: post
title:  "Computer/Server Upgrades & WSL2"
date:   2020-05-01 01:02:03 -0700
---
Computer Upgrade setup around end of June (AMD Ryzen 3700X, 32GB DDR4 3600Mhz, 2TB M.2 SSD, Asus Crosshair VII X470)

The Gaming Computer that was built in 2013 (Intel 4790S, 16GB DDR3 1866Mhz, 1TB M.2 SSD) 
became the new XCP-NG Server threw in 8GB from the old AMD FX server for a total of 24 GB DDR3 1866Mhz RAM.  New server built from scratch around July. Donated the old AMD FX CPU, Board, and Cooler to a friend who could use it so it doesn't just clutter up my apartment.

Now that I'm not stuck on an older version of Windows 10.  I can use some new features and the New Hyper-V Backend that Virtual Box Supports. Now you can use Hyper-V and Virtual box on the same machine depending on what you need.

<b>Update: I no longer use WSL or WSL2 as using Native Linux has more advantages.</b>

I also got WSL2 (Windows Subsystem for Linux 2) working as well on my laptop and desktop. It uses HyperV on the backend. It is much more useful than WSL 1 as you can use tools such as Nmap inside. WSL in general is usefully since you can use Linux tools on your local Windows files without having to transfer them to another machine. I also got the basic version of Windows Terminal working too so I can have multiple tabs of Powershell and Debian.

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\CSUW-1.webp" 
		alt="Windows Terminal Picture"
	>
</picture>

Windows terminal is so much better than putty for managing connection. In my opinion it also looks much easier on the eyes. I customized it a bit so the Windows terminal opens Linux by default and has a background.

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\CSUW-2.webp" 
		alt="Windows Terminal Picture 2"
	>
</picture>

Update: Windows Terminal now has an easier built in settings, where before it was strictly a .json file you had to edit.

Now that I had the spare parts to make a server. I setup XCP-NG based on Xen virtualization. I also setup Xen Orchestra (XOA) which is used to manage the VMs and Servers. Unfortunately I couldn't do much else with the server as it was maxed out on RAM just from XOA and a Terraria Game Server. I also had XOA built from sources so I could use all the features in my learning lab for free.

Links:
* <a href="https://xcp-ng.org/">XCP-NG</a>
* <a href="https://xen-orchestra.com/#!/xo-home">XOA</a>
