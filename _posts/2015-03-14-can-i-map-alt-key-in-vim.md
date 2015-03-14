---
layout: post
title: "Can I map Alt key in Vim?"
description: ""
category:
tags: []
---

Can I map Alt key in Vim?


I tried to map to as adding the below line to .vimrc, but it doesn't work. I checked the .vimrc is loaded by Vim.

`map <Alt-D> <C-D>`

is there any error in this mapping?


--------------------------------------- 
Map Alt Key in Vim on Mac:

Start by viewing the key code your terminal is sending to vim:

    $ sed -n l
    ^[[1;9D

In the above example, I ran the command and pressed <kbd>Alt + Left</kbd>.

The `^[[1;9D` is the escaped sequence being sent to vim, so we can user that for our mapping.

    map <Esc>[1;9D


