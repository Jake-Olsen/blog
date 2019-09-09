---
layout: post
title:  "Spanning Tree Root Problems"
date:   2019-08-16 01:02:03 -0700
---

This Friday there was a discussion with our Tier 3 Network Engineer after someone found 2 spanning tree roots and escalated the issue to him to ensure it was fixed correctly.

So what caused this?
<br>Here was a few of my thoughts:
<br>1) Were we running multiple trees such as PVSTP, or MSTP.
<br>&nbsp;&nbsp;&nbsp;Nope.
<br>2) Perhaps we are running 2 different spanning tree versions that aren't compatible?
<br>&nbsp;&nbsp;&nbsp;Nope
<br>3) Did STP get turned off on some ports?
<br>&nbsp;&nbsp;&nbsp;Yep STP got turned off on a few ports so multiple switches got elected to be the root bridge.

Some other real world issues I've seen is where an end user plugged in their own 5 port switch, which happened to have a priority of 4096. It became the root for the whole network. Everything had to route through the trunk, to their switch, then back through multiple trunks to get back to the router. Just for one way, then they have to go back through that long route for the return traffic. Along with the fact that a 5 port switch can't handle the traffic of a site with ten 48 port switches. 

Another example similar to the one above is where a Arris device (Probably a modem) became our STP Root.

We could have prevented this if we used bpdu filtering on the access ports. Which would prevent them from becoming part of our spanning tree, but would still allow network traffic through. Also it can help the security of your network since it will prevent STP information from going out of those ports aswell.
