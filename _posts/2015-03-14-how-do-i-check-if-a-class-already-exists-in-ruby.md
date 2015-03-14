---
layout: post
title: "How do I check If a Class already exists in Ruby"
description: ""
category:
tags: []
---

How do I check If a Class already exists in Ruby


How do I check If a Class already exists in Ruby,

My code is:

    puts "enter the name of the Class to see if it exists"   
    nameofclass=gets.chomp  
    eval (" #{nameofclass}...... Not sure what to write here")

I was thinking of using:

    eval "#{nameofclass}ancestors. ....."


--------------------------------------- 
    Kernel.const_defined?("Fixnum") # => true


