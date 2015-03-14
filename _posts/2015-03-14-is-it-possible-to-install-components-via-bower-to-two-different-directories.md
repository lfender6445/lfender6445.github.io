---
layout: post
title: "Is it possible to install components via bower to two different directories?"
description: ""
category:
tags: []
---

Is it possible to install components via bower to two different directories?


When using Sass and JS components, is it possible, or even, does it make sense to install them to different directories?

    .
    |-- app
  |-- scripts
      |-- components # js components go here
          |-- backbone-amd
          |-- etc
  |-- styles
      |-- modules
      |-- partials
      |-- components # sass components go here
          |-- normalize.scss
          |-- etc

What's the most efficient way to structure a project organized as such? Is there a good Grunt task to accomplish the goal of integrating bower installed sass components for a development environment?


--------------------------------------- 
There is a node package called [bower-installer](https://www.npmjs.org/package/bower-installer) that provides a single command for managing alternate install paths.

run `npm install -g bower-installer`

Set up your bower.json

    {
"name" : "test",
"version": "0.1",
"dependencies" : {
  "jquery-ui" : "latest"
},
"install" : {
  "path" : {
    "css": "src/css",
    "js": "src/js"
  },
  "sources" : {
    "jquery-ui" : [
      "components/jquery-ui/ui/jquery-ui.custom.js",
      "components/jquery-ui/themes/start/jquery-ui.css"
    ]
  }
}
    }

Then run `bower-installer` command.

This will install `components/jquery-ui/themes/start/jquery-ui.css` to `./src/css`, etc


