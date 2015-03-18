---
layout: post
title: "Where can I find the error logs of nginx?"
description: "Where can I find the error logs of nginx?"
permalink: "where-can-i-find-nginx-error-log"
category:
tags: ['nginx']
---

Where can I find the error logs of nginx, using fastcgi and django


i m using django with fastcgi + nginx.I want to know were the logs (error) are stored in this case


---------------------------------------
My ngninx log is located here:

    tail -f /usr/local/var/log/nginx/error.log

You can also check your `nginx.conf` to see if you have any directives dumping to custom log

    error_log /usr/local/var/log/nginx/error.log;
    error_log /usr/local/var/log/nginx/error.log notice;
    error_log /usr/local/var/log/nginx/error.log info;


