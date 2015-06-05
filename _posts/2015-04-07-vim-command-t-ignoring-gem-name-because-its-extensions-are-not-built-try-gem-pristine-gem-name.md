---
layout: post
title: "Vim/command-T: Ignoring “gem-name” because its extensions are not built. Try gem pristine “gem-name”"
description: "Vim/command-T: Ignoring “gem-name” because its extensions are not built. Try gem pristine “gem-name”"
category:
tags: ['vim', 'ruby']
permalink: vim-command-t-ignoring-gem-name-because-its-extensions-are-not-buil-try-gem-pristine/
---

Vim/command-T: Ignoring “gem-name” because its extensions are not built. Try gem pristine “gem-name”

Whenever I open the command-T plugin for the first time in MacVim, I get the following terminal:

    Ignoring atomic-1.1.13 because its extensions are not built. Try: gem pristine atomic-1.1.13
    Ignoring atomic-1.1.10 because its extensions are not built. Try: gem pristine atomic-1.1.10
    Ignoring bcrypt-3.1.7 because its extensions are not built. Try: gem pristine bcrypt-3.1.7
    Ignoring bcrypt-ruby-3.0.1 because its extensions are not built. Try: gem pristine bcrypt-ruby-3.0.1
    Ignoring eventmachine-1.0.3 because its extensions are not built. Try: gem pristine eventmachine-1.0.3
    Ignoring executable-hooks-1.3.2 because its extensions are not built. Try: gem pristine executable-hooks-1.3.2
    Ignoring ffi-1.9.3 because its extensions are not built. Try: gem pristine ffi-1.9.3
    Ignoring ffi-1.9.0 because its extensions are not built. Try: gem pristine ffi-1.9.0
    Ignoring ffi-1.4.0 because its extensions are not built. Try: gem pristine ffi-1.4.0
    Ignoring gem-wrappers-1.2.4 because its extensions are not built. Try: gem pristine gem-wrappers-1.2.4
    Ignoring json-1.8.1 because its extensions are not built. Try: gem pristine json-1.8.1
    Ignoring json-1.8.0 because its extensions are not built. Try: gem pristine json-1.8.0
    Ignoring nokogiri-1.6.3.1 because its extensions are not built. Try: gem pristine nokogiri-1.6.3.1
    Ignoring nokogiri-1.6.0 because its extensions are not built. Try: gem pristine nokogiri-1.6.0
    Ignoring nokogiri-1.5.6 because its extensions are not built. Try: gem pristine nokogiri-1.5.6
    Ignoring pg-0.17.1 because its extensions are not built. Try: gem pristine pg-0.17.1
    Ignoring pg-0.17.0 because its extensions are not built. Try: gem pristine pg-0.17.0
    Ignoring pg-0.15.1 because its extensions are not built. Try: gem pristine pg-0.15.1
    Ignoring pg-0.14.1 because its extensions are not built. Try: gem pristine pg-0.14.1
    Ignoring sqlite3-1.3.9 because its extensions are not built. Try: gem pristine sqlite3-1.3.9
    Ignoring sqlite3-1.3.8 because its extensions are not built. Try: gem pristine sqlite3-1.3.8
    Ignoring sqlite3-1.3.7 because its extensions are not built. Try: gem pristine sqlite3-1.3.7
    Ignoring thin-1.6.2 because its extensions are not built. Try: gem pristine thin-1.6.2

Any ideas?


---------------------------------------
I recently switched to from `rvm` to `chruby` and ran `gem update --system`, thats when the issue began occurring for me. After that, anytime I ran bundle I was slaughtered with the same warnings.

`Ignoring curb-0.8.6 because its extensions are not built. Try: gem pristine curb-0.8.6`

This, plus dozens of other warnings for other gems.

Not sure what fixed it, but I did 2 things and the warning disappeared:

    gem update bundler
    gem install curb


