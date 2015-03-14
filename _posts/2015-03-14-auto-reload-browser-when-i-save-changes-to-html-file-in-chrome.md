---
layout: post
title: "Auto-reload browser when I save changes to html file, in Chrome?"
description: ""
category:
tags: []
---

Auto-reload browser when I save changes to html file, in Chrome?


I'm editing an HTML file in Vim and I want the browser to refresh whenever the file underneath changes.

Is there a plugin for Google Chrome that will listen for changes to the file and auto refresh the page every time I save a change to the file? I know there's XRefresh for Firefox but I could not get XRefresh to run at all.

How hard would it be to write a script to do this myself?


--------------------------------------- 
The most flexible solution I've found is the [chrome LiveReload extension](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei?hl=en) paired with a [guard server](https://github.com/guard/guard-livereload).

Watch all files in a project, or only the ones you specify. Here is a sample Guardfile config:

    guard 'livereload' do
watch(%r{.*\.(css|js|html|markdown|md|yml)})
    end

The downside is that you have to set this up per project and it helps if you're familiar with ruby.

I have also used the Tincr chrome extension - but it appears to be tightly coupled to frameworks and file structures. (I tried wiring up tincr for a jekyll project but it only allowed me to watch a single file for changes, not accounting for includes, partial or layout changes). Tincr however, works great out of the box with projects like rails that have consistent and predefined file structures.

Tincr would be a great solution if it allowed all inclusive match patterns for reloading, but the project is still limited in its feature set.


