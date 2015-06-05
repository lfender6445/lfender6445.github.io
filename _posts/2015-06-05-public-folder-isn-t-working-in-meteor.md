---
layout: post
title: "Public folder isn't working in Meteor"
permalink: "public-folder-isnt-working-in-meteor/"
description: ""
category:
tags: ['javascript','meteor']
---


I'm trying to serve an image to my meteor app so I put the image in the public folder, but the image doesn't appears in the app (it shows only a broken image). But when I put the image in the root folder it works perfectly.

In other question related with this kind of problem I was that I should look in side the `app\_root/.meteor/build/static/`, but in my app I don't have any static folder inside the build folder

What could be the problem?


---------------------------------------
It's recommended you use `./public` directory for serving static assets.

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

> Files in /public are served to the client as-is. Use this to store assets such as images. For example, if you have an image located at /public/background.png, you can include it in your HTML with or in your CSS with background-image: url(/background.png). Note that /public is not part of the image URL.

[Official Meteor Docs - File Structure](https://docs.meteor.com/#/basic/filestructure)


