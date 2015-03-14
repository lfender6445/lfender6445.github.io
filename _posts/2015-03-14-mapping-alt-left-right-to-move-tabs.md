---
layout: post
title: "Mapping Alt + left|right to move tabs"
description: ""
category:
tags: []
---

Mapping Alt + left|right to move tabs


Ideally, I'd like `<A-left>` to execute `:tabmove -1` and `<A-right>` to execute `:tabmove +1`. However, when I put

    nnoremap <A-left> :tabmove -1<cr>
    nnoremap <A-right> :tabmove +1<cr>

in my .vimrc and try or , vim beeps and moves my cursor one character over in the direction I pressed. However, typing `:tabmove -1<cr>` directly into command mode gives the desired effect. How can I fix this? Thanks in advance.


--------------------------------------- 
Start by viewing the key code your terminal is sending to vim:

    $ sed -n l
    ^[[1;9D

In the above example, i ran the sed command and pressed <kbd>Alt + Left</kbd>.

The `^[[1;9D` is the escaped sequence being sent to vim, so we can user that for our mapping.

Add this to your .vimrc

    map <Esc>[1;9D :tabn<CR>

Now we can cycle through vim tabs by using <kbd>Alt + Left</kbd>


