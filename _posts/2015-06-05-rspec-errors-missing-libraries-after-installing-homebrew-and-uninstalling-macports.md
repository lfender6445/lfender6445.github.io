---
layout: post
title: "rspec errors, missing libraries after installing homebrew and uninstalling macports"
permalink: "rspec-errors-missing-libraries-after-installing-homebrew-and-uninstalling-macports/"
description: ""
category:
tags: ['homebrew']
---

I may have taken one step to far beyond my knowledge. I installed homebrew and after it continued to give me warnings about having macports installed I uninstalled that. But now my rspec tests don't run.

This is the errors I get.

    /Users/mark/.rvm/gems/ruby-1.9.2-p180/gems/nokogiri-1.4.4/lib/nokogiri.rb:13:in `require':
    dlopen(/Users/mark/.rvm/gems/ruby-1.9.2-p180/gems/nokogiri-1.4.4/lib/nokogiri/nokogiri.bundle, 9):
    Library not loaded: /opt/local/lib/libiconv.2.dylib (LoadError)
    Referenced from: /Users/mark/.rvm/gems/ruby-1.9.2-p180/gems/nokogiri-1.4.4/lib/nokogiri/nokogiri.bundle
    Reason: Incompatible library version: nokogiri.bundle requires version 8.0.0 or later,
    but libiconv.2.dylib provides version 7.0.0 -
    /Users/mark/.rvm/gems/ruby-1.9.2-p180/gems/nokogiri-1.4.4/lib/nokogiri/nokogiri.bundle

I've installed libiconv through homebrew but that didn't fix it. It's complaining about libiconv version numbers? Is this the problem?

---------------------------------------
FWIW, I ran into the same issue and if you are **vendorizing your gems, you will have to remove the offending gem from vendor/ruby** as a gem uninstall + reinstall is not always efficient. I'm guessing bundler leaves cache remnants of gems and their respective libs even when running a fresh install.


