---
layout: post
title: "How to change bower's default components folder?"
description: ""
category:
tags: []
---

How to change bower's default components folder?


I'm making a new project that uses bower from twitter. I created a `component.json` to maintain all my dependency like jquery. Then I run `bower install` that installs everything in a folder named `components`. But I need to install the components in a different folder, e.g. `public/components`.

I have tried editing my components.json into:

    {
"name": "test",
"version": "1.0.0",
"directory": "public/",
"dependencies": {
  "jquery": "*"
}
    }

or:

    {
"name": "test",
"version": "1.0.0",
"componentsDirectory": "public/",
"dependencies": {
  "jquery": "*"
}
    }

as shown in [https://github.com/twitter/bower/pull/94](https://github.com/twitter/bower/pull/94) but it doesn't work.


--------------------------------------- 
In addition to editing `.bowerrc` to setup your default install path, you can also setup custom install paths for different file types.

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

Run the following command: `bower-installer`

This will install `components/jquery-ui/themes/start/jquery-ui.css` to `./src/css`, etc


