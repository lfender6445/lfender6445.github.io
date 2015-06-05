---
layout: post
title: "why is curl slower than browser?"
permalink: "curl-slower-than-browser/"
description: "why is curl slower than browser?"
category:
tags: ['curl']
---

Why is curl slow than browser?

I am using [this class](http://semlabs.co.uk/journal/object-oriented-curl-class-with-multi-threading) to make one GET and another POST request to a website (the first request is to set a cookie). I am testing in a Win XP virtual machine with virtualbox, using wamp from wampserver dot com. The 2 requests takes from 10 to 18 seconds (with curl), but if I make those request directly via the webbrowser in that same virtual machine the website loads in just a few seconds, and it retrieves all the images, css, etc.

What could be causing curl to work so slow? is there a way to fix it?

---------------------------------------
I ran into this issue with a local web server. I was able to fix by adding

    ::1 localhost

to `/etc/hosts/` file.

This is the [ipv6 notation for 127.0.0.1](http://unix.stackexchange.com/questions/169518/what-does-this-host-means-1)


