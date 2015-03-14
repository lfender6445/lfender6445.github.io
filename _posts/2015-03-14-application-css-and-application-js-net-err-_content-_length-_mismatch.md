---
layout: post
title: "application.css and application.js net::ERR\_CONTENT\_LENGTH\_MISMATCH"
description: ""
category:
tags: []
---

application.css and application.js net::ERR\_CONTENT\_LENGTH\_MISMATCH


I just upgraded my nginx from 1.4.2 (/usr/local) to 1.4.7 (yum) on AWS EC2. I now have a pair of errors occuring on the client side:

    GET https://subdomain.mysite.com/assets/application.css net::ERR_CONTENT_LENGTH_MISMATCH 
    GET https://subdomain.mysite.com/assets/application.js net::ERR_CONTENT_LENGTH_MISMATCH

I am at a loss for this and google has not been much help. Any ideas on where to start? All help appreciated. Could the switch from a manual install to a yum install be the issue?


--------------------------------------- 
    tail -f /usr/local/var/log/nginx/error.log

You may see something like:

> "/usr/local/var/run/nginx/proxy\_temp/9/04/0000000049" failed (13: Permission denied) while reading upstream

Heres how I fixed:

    sudo nginx -s stop
    sudo rm -rf /usr/local/var/run/nginx/*


