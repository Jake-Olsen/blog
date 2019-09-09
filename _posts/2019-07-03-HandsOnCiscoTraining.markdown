---
layout: post
title:  "Hands On Cisco Training (Packet Tracer vs GNS3 vs Hardware)"
date:   2019-07-03 01:02:03 -0700
---
I’m starting to get more in depth into my cisco training. I think I've reached the point where Packet Tracer can no longer be used for everything my training. Mostly because the simulation software is missing features that I want to practice with to understand better. Along with some strange bugs that throws me off while I’m learning. 

A few recent bugs.
1. When in configuration mode and performing an action to multiple interfaces applies no config at all.  (int range gi0/0/0-1 doesn't apply certain configs)
2. Setting up link-local ipv6 addresses creates a permanent neighbor and route. Even after the ipv6 address is removed or changed. It cannot be cleared and will stay this way until the router is rebooted.

There are other bugs or features that don't fully work since it is a limited simulation, however I was able to learn most of the CCENT topics without the need of hardware. So, it was extremely useful up to this point.

I was looking into GNS3, but they don't include any cisco software. The IOSv is a bit expensive at $1000. If I wanted to use GNS3 economically and legally I could purchase hardware, then upload the IOS to my PC after looking through some GNS discussions. Basically, Cisco IOS can't be obtained and used for Free. You can either get a license or buy the hardware and "extract an IOS image (i.e. using TFTP) from a router you have access" 
 <a href="https://gns3.com/community/discussion/code-of-conduct-amp-gns3-faq">[2]</a> 

However, GN3 doesn't support all Cisco IOS, so it looks like the better option in the short term would to buy the hardware and just use it directly.

For the past few days I've just been looking into what hardware I should buy that I could use for what is left of my ICND1 and ICND2 course. One of my friends led me to this site that shows the "topics" that will be tested.  
<https://learningnetwork.cisco.com/community/certifications/ccent/icnd1/exam-topics>
<https://learningnetwork.cisco.com/community/certifications/ccna/icnd2/exam-topics>

So, I've been looking through eBay at Cisco hardware then looking up documentation to see what will cover most of it.
Some coworkers recommended I also take a look at the Cisco 800 series

Here are some of the resources I found along the way while looking for a solution  

\[1] [GNS3: Are Cisco IOS images necessary?]
 
\[2] [GNS3: Code of Conduct & FAQ]

\[3] [Cisco 1941 ISR Data Sheet]

\[4] [Cisco 1921 ISR (Sec-K9) Data Sheet]

\[5] [Cisco 877 Data Sheet]



[GNS3: Are Cisco IOS images necessary?]: https://gns3.com/discussions/are-cisco-ios-images-necessary-a
[GNS3: Code of Conduct & FAQ]: https://gns3.com/community/discussion/code-of-conduct-amp-gns3-faq
[Cisco 1941 ISR Data Sheet]: https://www.cisco.com/c/en/us/products/collateral/routers/1900-series-integrated-services-routers-isr/data_sheet_c78_556319.html
[Cisco 1921 ISR (Sec-K9) Data Sheet]: https://www.cisco.com/c/en/us/products/collateral/routers/1900-series-integrated-services-routers-isr/data_sheet_c78-598389.html
[Cisco 877 Data Sheet]: https://www.cisco.com/c/en/us/products/collateral/routers/800-series-routers/product_data_sheet0900aecd8028a976.html
