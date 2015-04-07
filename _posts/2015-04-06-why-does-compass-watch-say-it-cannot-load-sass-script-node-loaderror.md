---
layout: post
title: "Why does “compass watch” say it cannot load sass/script/node (LoadError)?"
description: "compass watch cannot load sass script node"
permalink: /compass-watch-cannot-load-sass-script-node/
category:
tags: ['compass']
---

Why does “compass watch” say it cannot load sass/script/node (LoadError)?


I'm having a problem with my compass watch command - it worked fine up until a few days ago. I have made no changes to my config files.

I reinstalled Compass, used rvm to update Ruby. I checked my custom\_require.rb file but I really don't know what to look for. It seems to be trying to load the file "sass/script/node" somewhere and from `http://sass-lang.com/docs/yardoc/Sass/Script/Node.html` I gather the filepath - but I have nothing there.

    /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:60:in `require': cannot load such file -- sass/script/node (LoadError)
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:60:in `rescue in require'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:35:in `require'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass/sass_extensions/monkey_patches/browser_support.rb:1:in `<top (required)>'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass/sass_extensions/monkey_patches.rb:2:in `block in <top (required)>'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass/sass_extensions/monkey_patches.rb:1:in `each'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass/sass_extensions/monkey_patches.rb:1:in `<top (required)>'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass/sass_extensions.rb:9:in `<top (required)>'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass.rb:5:in `block in <top (required)>'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass.rb:4:in `each'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/lib/compass.rb:4:in `<top (required)>'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/rubies/ruby-1.9.3-p194/lib/ruby/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/bin/compass:20:in `block in <top (required)>'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/bin/compass:8:in `fallback_load_path'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/gems/compass-0.12.2/bin/compass:19:in `<top (required)>'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/bin/compass:19:in `load'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/bin/compass:19:in `<main>'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/bin/ruby_noexec_wrapper:14:in `eval'
from /Users/sampurcell/.rvm/gems/ruby-1.9.3-p194/bin/ruby_noexec_wrapper:14:in `<main>'

Anyone have any ideas?


---------------------------------------
I believe this is due to versioning conflicts with sass.

[https://rubygems.org/gems/compass](https://rubygems.org/gems/compass) gem is currently at `v0.12.16` currently - add this to Gemfile

    gem 'sass', '3.2.19'
    gem 'compass', '0.12.6'

You may be required to uninstall all versions of both gems first.


