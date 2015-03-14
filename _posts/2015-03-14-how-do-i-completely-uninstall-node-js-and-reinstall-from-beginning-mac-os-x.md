---
layout: post
title: "How do I completely uninstall Node.js, and reinstall from beginning (Mac OS X)"
description: ""
category:
tags: []
---

How do I completely uninstall Node.js, and reinstall from beginning (Mac OS X)


My version of node is always v0.6.1-pre even after I install brew node and NVM install v0.6.19.

My node version is:

    node -v
    v0.6.1-pre

NVM says this (after I install a version of node for the first time in one bash terminal):

    nvm ls
    v0.6.19
    current: v0.6.19

But when I restart bash, this is what I see:

    nvm ls
    v0.6.19
    current: v0.6.1-pre
    default -> 0.6.19 (-> v0.6.19)

So where is this phantom node 0.6.1-pre version and how can I get rid of it? I'm trying to install libraries via NPM so that I can work on a project.

I tried using BREW to update before NVM, using "brew update" and "brew install node". I've tried deleting the "node" directory in my /usr/local/include and the "node" and "node\_modules" in my "/usr/local/lib". I've tried uninstalling npm and reinstalling it following these instructions: [http://superuser.com/questions/268946/uninstall-node-js](http://superuser.com/questions/268946/uninstall-node-js)

All of this because I was trying to update an older version of node to install the "zipstream" library. Now there's folders in my users directory, and the node version STILL isn't up to date, even though NVM says it's using 0.6.19.

**Ideally, I'd like to uninstall nodejs, npm, and nvm, and just reinstall the entire thing from scratch on my system.**


--------------------------------------- 
 **For brew users, OSX** :

    brew uninstall node
    brew prune
    rm -f /usr/local/bin/npm
    rm -f /usr/local/lib/dtrace/node.d
    rm -rf ~/.npm

then

    brew install node
    which node #=> /usr/local/bin/node


