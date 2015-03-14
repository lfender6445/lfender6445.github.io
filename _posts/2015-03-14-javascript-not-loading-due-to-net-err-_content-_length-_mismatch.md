---
layout: post
title: "Javascript not loading due to net::ERR\_CONTENT\_LENGTH\_MISMATCH"
description: ""
category:
tags: []
---

Javascript not loading due to net::ERR\_CONTENT\_LENGTH\_MISMATCH


I've got an app that runs fine locally, but barfs in production. (Classic problem, right?)

In production, the JS isn't firing correctly. When I open up the browser console, I see this error:

`net::ERR_CONTENT_LENGTH_MISMATCH`

When I look in the network tab of Developer Tools, is shows that it failed on a GET request for text/html.

It's a cryptic error. I've only found two other SO posts that even mention is and they're unsolved. (For the interested: [first post](http://stackoverflow.com/questions/22341884/rails-image-disappears-with-error-failed-to-load-resource-neterr-content-len) and [second post](http://stackoverflow.com/questions/22183859/javascript-err-content-length-mismatch))

Any idea (1) what it means or (2) how to resolve it?


--------------------------------------- 
Had the same issue here, but mine was in development - for me the problem lay somewhere between nginx and file permissions:

    tail -f /usr/local/var/log/nginx/error.log

Refresh your asset, eg `http://localhost:3000/assets/jquery/jquery.js`

You may see something like:

> "/usr/local/var/run/nginx/proxy\_temp/9/04/0000000049" failed (13: Permission denied) while reading upstream for file xyz

Heres how I fixed:

    sudo nginx -s stop
    sudo rm -rf /usr/local/var/run/nginx/*
    sudo nginx

Have a look at your server logs to determine what the real issue is.


