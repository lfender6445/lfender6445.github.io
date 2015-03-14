---
layout: post
title: "Meteor public folder not working"
description: ""
category:
tags: []
---

Meteor public folder not working


I'm new to Meteor and I'm trying to understand how to serve static content - images, JS, etc.. I've followed the docs by creating the correct folder structure (which it doesn't really touch on) but making requests to this content just fails over to serving the main app page instead.

For instance - putting an image in "app\_root"/public/image.png and making a request to localhost:3000/image.png just returns the main app page.

Any clue what I'm doing wrong here? Thanks!


--------------------------------------- 
Use `./public` directory for serving static assets.

Given the following directory structure:

    - server
    - client
    - public
- css
  - bootstrap.css
- images
- js

You could serve the static assets by dropping 'public' from linked documents.

`<link href='/css/bootstrap.css'>`

More info here: [Official Meteor Docs #FileStructure](https://docs.meteor.com/#/basic/filestructure)

> Files in /public are served to the client as-is. Use this to store assets such as images. For example, if you have an image located at /public/background.png, you can include it in your HTML with or in your CSS with background-image: url(/background.png). Note that /public is not part of the image URL.
