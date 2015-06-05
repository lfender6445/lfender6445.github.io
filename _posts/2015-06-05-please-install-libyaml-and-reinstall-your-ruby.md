---
layout: post
title: "Please install libyaml and reinstall your ruby"
description: ""
category:
tags: []
---

Please install libyaml and reinstall your ruby


libyaml warning doesn't go away, even if you install libyaml

    gem install bundler
    /home/ec2-user/.rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/yaml.rb:56:in `<top (required)>':
    It seems your ruby installation is missing psych (for YAML output).
    To eliminate this warning, please install libyaml and reinstall your ruby.
    Fetching: bundler-1.3.4.gem (100%)
    Successfully installed bundler-1.3.4


--------------------------------------- 
A friend of mine had a similar problem on his mac.

`brew install libyaml`

ended up working for us and we were able to avoid a reinstall of ruby.


