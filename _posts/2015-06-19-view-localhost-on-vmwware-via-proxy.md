---
layout: post
title: "view localhost on vmwware via proxy"
description: ""
category:
tags: []
---

Would you ike to view your host machines localhost in a virtualized machine? What aboud a fully quaified domain, such as local.example.com, a URL that sits behind nginx and is pointing from localhost to port 9292. As browser diversity challeneges the most seasons javascript developers, usage of virtual machines attemp to sooth and mediate challenges in networking and communication, namely ip resoution. So what are your options? Lets start with the simplest:

localhost on host machine should be avaialable on the virtual box

this can be accomplished in many ways. We will discuss 3, and none of them will involve a proxy.
# Private IP
Start by obtaining your host machines private ip

this private ip is exposed for all machines on the same network and available in a browser - it can be found my openening your networking preferences and grabbing the visible IP address or typing ifconfig into your terminal - look at the IP address embedded in your en0 or en1 interfaces.

For this example, my private network IP is 192.187.1.137. Your wills be similar but different.

# Next, we will attempt to point our windows virtualbox to look to this IP as means of routing localhost. Simple enough:

view 192.187.137 in your browser. Assuming nginx is running, you should see its starter page.
If you are on the same network from an android or iphone, I encourage you to check there as well -this IP is available to all machines on the private network (assuming wifi) and able to access the host machines `localhost`

# Using OUTER
Virtualbox autmoatically expoes 1.0.2.2 as an IP to delegate back to the host machine.

on your virtualbox in # c:\Windows\System32\Drivers\etc\hosts type
1.0.2.2 localhost

assuming no proxies, the following will resolve to the loopback address allowing the 2 mahchines on the private network to comunciate with one another, request, respond,etc.

now you can access localhost:9292 from vbox, thus sending request to the host machine

# usning proxies for fully qualified domains

open charles
enable mac proxy with port set to 8888
get your private network ip, something ike 192.168.1.37
load VM ie8, open browser setting and create a lan proxy that routes traffic to 192.168.1.3.7:8888
traffic should now be routed through charles, which return network data from host machine
hit a fully qualified host name as served by nginx x, such as local.apartmentguide.com
ensure everything is working properly
