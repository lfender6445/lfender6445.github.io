---
layout: post
title: "Is there a tool to remove unused methods in javascript?"
description: ""
category:
tags: []
---

Is there a tool to remove unused methods in javascript?


I've got a collection of javascript files from a 3rd party, and I'd like to remove all the unused methods to get size down to a more reasonable level.

Does anyone know of a tool that does this for Javascript? At the very least give a list of unused/used methods, so I could do the manually trimming? This would be in addition to running something like the YUI Javascript compressor tool...

Otherwise my thought is to write a perl script to attempt to help me do this.


--------------------------------------- 
    npm install -g fixmyjs
    fixmyjs <filename or folder>

A configurable module that uses jshint to flag functions that are unused and perform clean up as well.

github: [https://github.com/jshint/fixmyjs](https://github.com/jshint/fixmyjs)

jshint info: [http://www.jshint.com/docs/](http://www.jshint.com/docs/)

I am honestly not sure that it removes undefined functions as opposed to flagging them, but it is a great tool for cleanup.

There is also the google closure compiler which claims to remove dead JS but this is more of a build tool [https://developers.google.com/closure/compiler/](https://developers.google.com/closure/compiler/)


