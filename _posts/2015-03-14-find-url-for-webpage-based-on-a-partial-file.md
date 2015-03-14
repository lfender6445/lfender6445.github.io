---
layout: post
title: "Find url for webpage based on a partial file"
description: ""
category:
tags: []
---

Find url for webpage based on a partial file


I was introduced to a large team and not very familiar with the site I am developing for. I need to make an edit to a partial (i.e. \_partial\_file.html.haml) and need to verify the change visually but I don't know where that partial is being displayed on the website. Is there a way I can get a url from a partial file with rails.

For example, could I run a rake routes | grep or do something in the rails console to help find any URL where the partial is displayed?

Thanks


--------------------------------------- 
When you render a page you should see output in the console for all templates being rendered.

example `rendering template show.html.haml from SomeController#index`

Use this to locate the template that is including your partial. You can then use that to search the entire project for all templates including that partial.

Rails renders templates by a specific convention that maps controller methods to specific layouts and templates. I would familiarize yourself with [http://guides.rubyonrails.org/layouts\_and\_rendering.html](http://guides.rubyonrails.org/layouts_and_rendering.html) to get a better idea of how the default internals work for you rails app and use that as a starting point.


