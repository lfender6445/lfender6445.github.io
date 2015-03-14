---
layout: post
title: "Global rescue and logging exceptions in Sinatra"
description: ""
category:
tags: []
---

Global rescue and logging exceptions in Sinatra


How do I specify a global rescue in case of an exception, and if you use Sinatra for an API or application, how do you handle logging?


--------------------------------------- 
I had trouble getting this working out of the box in my dev environment - to get it to work, I had to set show\_exceptions to false in my sinatra config.

    class BaseApp < Sinatra::Base
    
    
configure { set :show_exceptions, false }
    
    
error do |err|
  raise "Error: #{err}"
end
    
    
    end

This setting, when set to true, enables error pages that show backtrace and environment information when an unhanded exception occurs, but I could only fire custom errors by disabling it.


