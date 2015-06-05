---
layout: post
title: "net::ERR\_CONTENT\_LENGTH\_MISMATCH"
description: "how to fix net err content length mismatch"
category:
tags: ['nginx']
permalink: 'application-net-err-content-length-mismatch/'
---

Content length errors occur when there is a byte difference between the size of the response in the header compared to the actual size of the response document.

> "Content-Length mismatch: Response Header claimed 1767884 bytes, but server sent 1772317 bytes."

Recently, these issues began creeping up for me in a few rails + sinatra projects and I had recently upgrade nginx.

    GET https://subdomain.mysite.com/assets/application.css net::ERR_CONTENT_LENGTH_MISMATCH
    GET https://subdomain.mysite.com/assets/application.js net::ERR_CONTENT_LENGTH_MISMATCH

Thats when theses issues started appearing on the client side.

---------------------------------------

Start by taking a look at your HTTP servers logs:

    tail -f /usr/local/var/log/nginx/error.log

Refresh your asset - you may see something like:

> "/usr/local/var/run/nginx/proxy\_temp/9/04/0000000049" failed (13: Permission denied) while reading upstream

Heres how I fixed:

    sudo nginx -s stop
    sudo rm -rf /usr/local/var/run/nginx/*

The `/usr/local/var/run/nginx` directory holds tmp data describing nginx since it was booted. Files under this directory are removed at the beginning of the boot process and can be safeley deleted.

---------------------------------------

Have you made any changes to your server configuration recently?

If all else fails, clear out stale assets and try restarting your http server.
