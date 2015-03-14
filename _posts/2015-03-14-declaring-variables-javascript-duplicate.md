---
layout: post
title: "Declaring variables javascript [duplicate]"
description: ""
category:
tags: []
---

Declaring variables javascript [duplicate]


This question already has an answer here:

- [Why would a JavaScript variable start with a dollar sign?](/questions/205853/why-would-a-javascript-variable-start-with-a-dollar-sign) 14 answers 

I just have a quick question and cant find anything on google. I was going through some code another programmer put together and he declares ALL of his javascript variables with $ in front of them...for instance:

    var $secondary;

Is there a reason for this? Could this cause problems in the future if JQuery ever ends up being used. I'm just curious because I was going to clean it up if so.


--------------------------------------- 
its just a convention for jQuery DOM selctions.

    var $logo = $('a.logo');

it wont cause any issues - it just lets other devs know that you're working with a jQuery wrapped dom element.


