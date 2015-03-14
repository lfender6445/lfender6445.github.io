---
layout: post
title: "How to use Pry with Sinatra?"
description: ""
category:
tags: []
---

How to use Pry with Sinatra?


I am writing my first Sinatra application and would like to use Pry to inspect/debug some things going on in the application. I haven't used Pry before either, but I would like to try it out. How would I get started using Pry with my Sinatra application?


--------------------------------------- 
 **load the application into a pry session** :

take a look at your config.ru - lets say it looks something like this:

    require File.join(File.dirname( __FILE__ ), 'config', 'application.rb')

you can load your application into pry using `pry -I . -r config/application.rb`


