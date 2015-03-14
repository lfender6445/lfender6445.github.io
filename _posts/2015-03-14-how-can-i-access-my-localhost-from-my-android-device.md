---
layout: post
title: "How can I access my localhost from my Android device?"
description: ""
category:
tags: []
---

How can I access my localhost from my Android device?


Am able to access my laptop web server using the Android emulator, am using `10.0.2.2:portno`works well.

But when I connect my real Android phone, the phone browser cannot connect to the same web server on my laptop. The phone is connected to the laptop using a USB cable. If I run the adb devices command, I can see my phone.

What am I missing?


--------------------------------------- 
on mac osx, i had success by enabling remote management:

> 1. ensure your phone and laptop are connected to the same wifi network
> 2. on mac, goto system preferences/sharing 
> 3. make sure `remote management`is checked

You should see a message similar to this

> Other users can manage your computer using the address `some.url.com`

On your android device you should now be able to hit `some.url.com`, which delegates to `localhost` on your mac.


