---
layout: post
title: "is it possible to mapping Alt-hjkl in Insert mode?"
description: ""
category:
tags: []
---

is it possible to mapping Alt-hjkl in Insert mode?


before describing my problem, I'd list the env. applications here:

    OS:linux 2.6.37-ARCH (archlinux i686)
    vim: 7.2.436
    Terminal emulator: urxvt (with 256colors patch)
    
    
    kent$ echo $TERM
    rxvt-256color
    
    
    screen: Screen version 4.00.03 (FAU) 23-Oct-06

I run vim in terminal. I want to move cursor in INSERT mode by pressing ALT-hjkl, after the cursor moved, stay in INSERT mode, so that I could continue typing words.

articles I found:

[http://vim.wikia.com/wiki/Mapping\_fast\_keycodes\_in\_terminal\_Vim](http://vim.wikia.com/wiki/Mapping_fast_keycodes_in_terminal_Vim)

[http://vim.wikia.com/wiki/Get\_Alt\_key\_to\_work\_in\_terminal](http://vim.wikia.com/wiki/Get_Alt_key_to_work_in_terminal)

what I tried:

in .vimrc do a keyCode mapping with ttimeoutlen=50 like this: ( only alt-j mapping was pasted as example):

    set timeout ttimeoutlen=50
    set <F13>=^[j "ctrl-v alt-j
    imap <F13> <down>

with this conf, moving cursor in INSERT mode was ok. If I press `<ESC>` and j. Vim brings me back to insert Mode. I don't know why the `ttimeoutlen=50` didn't work.

also tried:

    set timeout ttimeoutlen=50
    set <M-j>=^[j

With this setting, when I pressed ALT-j, a "e" with an accent mark was typed.

Can you guys give me any hints how should I map the ALT-hjkl in terminal ?

Thanks in advance

Kent


--------------------------------------- 
For arrow keys:

Start by viewing the key code your terminal is sending to vim:

    $ sed -n l
    ^[[1;9D

In the above example, i ran the sed command and pressed <kbd>Alt + Left</kbd>.

The `^[[1;9D` is the escaped sequence being sent to vim, so we can user that for our mapping.

Add this to your .vimrc

    map <Esc>[1;9D :tabn<CR>

Now we can cycle through vim tabs by using <kbd>Alt + Left</kbd>


