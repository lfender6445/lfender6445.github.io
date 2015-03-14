---
layout: post
title: "nginx - nginx: [emerg] bind() to [::]:80 failed (98: Address already in use) [closed]"
description: ""
category:
tags: []
---

nginx - nginx: [emerg] bind() to [::]:80 failed (98: Address already in use) [closed]


All of a sudden I am getting the below nginx error

    * Restarting nginx
     * Stopping nginx nginx
 ...done.
     * Starting nginx nginx
    nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
    nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
    nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
    nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
    nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
    nginx: [emerg] still could not bind()
 ...done.
 ...done.

If I run

    lsof -i :80 or sudo fuser -k 80/tcp

I get nothing. Nothing on port 80

Then I run the below:

    sudo netstat -pan | grep ":80"
    tcp 0 0 127.0.0.1:8070 0.0.0.0:* LISTEN 15056/uwsgi     
    tcp 0 0 10.170.35.97:39567 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39564 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39584 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39566 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39571 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39580 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39562 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39582 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39586 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39575 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39579 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39560 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39587 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39591 10.158.58.13:8080 TIME_WAIT -               
    tcp 0 0 10.170.35.97:39589 10.158.58.13:8080 TIME_WAIT -

I am stumped.

How to a debug?

I am using uwsgi with a

proxy pass on port 8070. uwsgi is running. Nginx is not. I am using ubuntu 12.4

Below are the relevant portions of my nginx conf file

    upstream uwsgi_frontend {
        server 127.0.0.1:8070;
      }
    server {
    listen 80;
      server_name 127.0.0.1;
      location = /favicon.ico {
                log_not_found off;
              }
    
    
    
    
    
    
              location / {
                     include uwsgi_params;
                     uwsgi_buffering off;
    
    
                     uwsgi_pass 127.0.0.1:8070;
               }
      }

Here is how I install nginx on ubuntu 12.04

    nginx=stable;add-apt-repository ppa:nginx/$nginx;
    apt-get update
    apt get install nginx-full


--------------------------------------- 
i fixed this by running `sudo apachectl stop`. turns out apache was running in the background and prevented nginx from starting on the desired port.


