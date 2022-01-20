---
layout: post
title:  "Docker Containers"
date:   2020-07-22 01:02:03 -0700
---

Started learning about what Docker is as I am in the process of migrating my Unifi Network Controller to the XCP-NG Xen Server rather than it being inside a VirtualBox VM on my Gaming Desktop. I also learned that docker can complicate a setup if you aren't well versed in it, and it is highly recommended to not use a docker image that is not maintained on an official basis. So I ended up abandoning the idea of using Unifi Controller inside docker as it required tons of work arounds and it had no official support from Unifi.


Useful information on how Docker is different from a virtual machine when you want to run multiple applications within containers that don't interfere with each other. Along with other beginner information I found useful when I started learning about this topic.
<br><https://stackoverflow.com/questions/16047306/how-is-docker-different-from-a-virtual-machine>
<br><https://docs.docker.com/engine/faq/>
<br><https://docs.docker.com/network/bridge/>