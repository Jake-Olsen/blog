---
layout: post
title:  "Chrome Web Serial"
date:   2021-10-30 01:02:03 -0700
---

The chrome development team has come up with something pretty cool.
A way to manipulate serial ports on your computer in a web browser. I first found out during a live stream on YouTube where someone was discussing a new way to flash Arduino binaries. 

Then a few days later I was hooking back up my lab router to start self studying again and wondered if there was a way to connect the serial terminal session over the web browser instead of using the old way of finding the COM port then loading up putty and setting the COM port manually. Then I found it there is a way to use it, and it's out of the experimental phase already! You just need to have a web page coded to ask for the serial port.
<br><https://web.dev/serial/>

Google actually has a live version on GitHub. Wouldn't recommend using it in production. You should generally host your own if you are going to use it in production.
<br><https://googlechromelabs.github.io/serial-terminal/>

At this time it even works in Edge with no additional config and automatically figures out the available Serial COM ports.

<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\ChromeWebSerial-1.webp" 
		alt="X"
	>
</picture>

Used it to reset my lab pfsense router back to default.
<picture>
	<img 
		src="{{site.url}}{{site.baseurl}}\assets\images\ChromeWebSerial-2.webp" 
		alt="X"
	>
</picture>
