---
layout: post
title: "10 Must Have Chrome Extensions for Developers 2014"
description: ""
category: development
tags: [chrome, development, productivity]
permalink: /10-must-have-chrome-extensions-for-developers-2014/
---

A DRY work flow is crucial in development. In the time I've been programming, I've collected a few chrome extensions that are essential to my development work flow and that make both my professional and personal life in the browser much easier.

* ## LiveReload

  LiveReload allows you to detect changes on your file system and reloads the pages to reflect current changes. It receives messages from a Guard server running in your project root and is highly configurable, using regular expressions to reload the browser when files of your choice have changed. The downside is you have to configure a guard server in tandem with the plugin, but it is BY FAR the most flexible solution I've found.

  All thats left is to enable LiveReload for your current page and start the Guard server!

  [Get LiveReload](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei){: class='grn'}
  [Get Guard LiveReload](https://github.com/guard/guard-livereload){: class='grn'}

  An alternative to LiveReload for simpler projects is [Tincr](https://chrome.google.com/webstore/detail/tincr/lfjbhpnjiajjgnjganiaggebdhhpnbih), which creates a new panel in the chrome dev tools to toggle reloading against a specific page or file.


* ## Vimium
  Users of the vim text editor will love this extension. Time is everything. The less time I have to spend using the mouse the better. I discovered Vimium a few days ago and it is nothing short of amazing, adding sensible vim like bindings to any web page. This is especially useful for repetitive tasks, navigation, and tab management.

  Here are a few of my favorite bindings:

    >
      gg      scroll to top of the page
      G       scroll to bottom of the page
      f       open a link in the current tab
      F       open a link in a new tab
      r       reload
      gs      view source
      yy      copy the current url to the clipboard
      yf      copy a link url to the clipboard
      o       Open URL, bookmark, or history entry
      O       Open URL, bookmark, history entry in a new tab
      b       Open bookmark
      B       Open bookmark in a new tab


  I've only scratched the surface - check out the source code for more information

  [Get Vimium Chrome Extension](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb){: class='grn'}
  [Vimium Documentation](https://github.com/philc/vimium/){: class='grn'}


* ## Postman - REST Client

  The web is and has been moving to a service centric model for a while now. It's hard to be a developer these days without relying on some XML or JSON based rest API at least once. Postman makes it easy to craft and record API calls to the services your rely on the most.

  You can separate these calls in their own unique collections, split url query params in a visually sensible way, and execute everything from PUT, to PATCH, to DELETE.

  [Get Postman Chrome Extension](https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm?hl=en){: class='grn'}
* ## JSONView

  Chrome, for whatver reason, doesn't render JSON in a sensible way.

  JSONView supports syntax highlighting and the collapsing and nesting of JSON responses.

  [Get JSONView Chrome Extension](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en){: class='grn'}

* ## Hacker Vision
  The web is traditionally built with black text on a stark white background. As a developer, it can be straining to make the visual context switch between these contrasts.


  HackerVision is an extension that injects CSS into your current page, using a formula to invert colors and apply terminal like shading to the body and text, making pages much easier to read, thus reducing eye strain  Another plugin, [deuluminate](https://chrome.google.com/webstore/detail/deluminate/iebboopaeangfpceklajfohhbpkkfiaa?hl=en-US) works in a similar way.

  The plugin binds to `cmd + shift + f11`, allowing you to easily toggle hacker vision on and off. You also have the ability to disable hacker vision for specific plugins and pages.

  [Get Hacker Vision Chrome Extension](https://chrome.google.com/webstore/detail/hacker-vision/fommidcneendjonelhhhkmoekeicedej?hl=en-US){:class='grn'}

* ## DevTools Theme: Zero Dark Matrix
  If you spend a lot of time in the chrome web inspector, then this plugin is for you. Based on a molokai like colorscheme, this plugin restyles your dev console so it is more in line with a traditional dev themed text editor that will feel very familiar to users of Vim or Sublime. Because the web inspector itself is just HTML and CSS, this re-skin attempts to re-craft the console for ease of use and access, where panels have logical placement and are easily resized.

  There are some nice CSS3 animations that come with the plugin as well, giving an accordion and drawer like feel to chrome dev tools.

  [Get Zero Dark Matrix Chrome DevTools Theme](https://chrome.google.com/webstore/detail/devtools-theme-zero-dark/bomhdjeadceaggdgfoefmpeafkjhegbo?hl=en-US){:class='grn'}

* ## Workflowy

  TODO list apps are everywhere. The free version even syncs up with my email. Workflowy makes making lists fun again (make lists not war!). Its a simple app equipped with powerful key bindings and is something I use both in personal and professional life.

  For what its worth, I prefer the web client to the chrome extension.

  [Get Workflowy Chrome Extension](https://chrome.google.com/webstore/detail/workflowy/koegeopamaoljbmhnfjbclbocehhgmkm?hl=en-US){:class='grn'}

* ## Appspector
  This plugin allows you to detect web applications and javascript libraries that are running on a specific website. I keep this one installed
mostly to gauge what libraries my favorite sites are using - it also does a good job of detecting blogging platforms or frameworks like WordPress and Joomla.
[Get Appspector Chrome Extension](https://chrome.google.com/webstore/detail/appspector/homgcnaoacgigpkkljjjekpignblkeae?hl=en){:class='grn'}

* ## Tab Pinner
  Chrome treats pinned tabs differently - if chrome is ever shut down or crashes, pinned tabs are reopened by default.

  I find Chromes 'pin tab' feature to be quite useful. Unfortunately, chrome is not equipped with a key binding that allows me to easily pin tabs. Tab pinner allows the user to easily pin and unpin tabs with `cmd + shift + x`.

  [Get Tab Pinner Chrome Extension](https://chrome.google.com/webstore/detail/tab-pinner-keyboard-short/mbcjcnomlakhkechnbhmfjhnnllpbmlh?hl=en){:class='grn'}

* ## Ruby Omniref
  As a ruby developer, I find this tool to be extremely useful:

  > "The Omniref addon integrates Ruby documentation search results from Omniref.com into your Google search results, and automatically annotates Ruby source listings on Github with links to documentation searches on Omniref."

  It would be nice to see more extensions like this geared towards other languages.
  [Get Ruby Omniref Chrome Extension](https://chrome.google.com/webstore/detail/omniref/jgkfbhdcoimcmlnebfnggkegaincacgj?hl=en){:class='grn'}

## Some Extras

This was supposed to be a list of 10 extensions but what the hell. Lets make it 12

  * ### LastPass

    LastPass is amazing. With lastpass I can automate logins across all of my devices and customize each page or entry under a single master password, saving me the headache of having to remember every unique password combination I possess for a site. I could not live without this plugin.

    [Get LastPass Chrome Extension](https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd?hl=en-US){:class='grn'}

  * ### Check My Links

    This plugin is more suited towards bloggers, but it allows you to verify that all of the links on your page or post are working as intended. Useful for drafting and publishing content.

    [Get Check my Links Chrome Extension](https://chrome.google.com/webstore/detail/check-my-links/ojkcdipcgfaekbeaelaapakgnjflfglf){:class='grn'}
