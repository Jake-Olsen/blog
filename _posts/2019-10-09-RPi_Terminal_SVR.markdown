---
layout: post
title:  "Raspberry Pi Terminal Server"
date:   2019-10-09 01:02:03 -0700
---
I liked the idea that I found on this blog post, so I looked a bit further into it.
<https://blog.jasons.org/2016/04/29/raspberry-pi-3-terminal-server/>

I got it setup and working on my Raspberry Pi 3b+ that I was previously using as just a test device for the lab. 

I decided to just use the same [UGREEN USB to 4 Serial RS232 DB9 Cable]( https://www.ugreen.com/product/UGREEN_USB_to_Serial_RS232_9Pin_Male_to_Male_Cable_Adapter_4_Ports-en.html) from the blog post, along with a cheap bundle of four Serial to RJ45 Console cables. Then I'll just add my 1 cable I had before for a total of 5 so I'll have full access again.


The Setup:
-------------------------------

Install Serial to network proxy:
```
apt install ser2net
```

Find the USB serial device path:
```
jake@raspberrypi:~ $ ls /dev | grep ttyUSB
ttyUSB0
ttyUSB1
ttyUSB2
ttyUSB3
ttyUSB4
```

Edit the config file
/etc/ser2net.conf

I slightly altered the default for my use case.
<br>Updated Config October 12th
```
##USB SERIAL x4 HUB###########
#Router_1
7000:telnet:1200:/dev/ttyUSB0
#Router_2
7001:telnet:1200:/dev/ttyUSB1
#
#Switch_1
7002:telnet:1200:/dev/ttyUSB2
#Switch_2
7003:telnet:1200:/dev/ttyUSB3
##############################
#
##USB SERIAL Single
#Router 3
7004:telnet:1200:/dev/ttyUSB4
```
Start the service
```
sudo systemctl start ser2net
```
Connect to the reverse telnet session.
To end it press Ctrl + ] then type close
```
jake@raspberrypi:~ $ telnet localhost 2001
Trying ::1...
Connected to localhost.
Escape character is '^]'.
R1>
telnet> close
Connection closed.
jake@raspberrypi:~ $
```


