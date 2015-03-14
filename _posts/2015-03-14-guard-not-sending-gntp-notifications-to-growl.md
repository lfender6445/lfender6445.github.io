---
layout: post
title: "Guard not sending gntp notifications to growl"
description: ""
category:
tags: []
---

Guard not sending gntp notifications to growl


I am using guard with minitest, and everything works great except growl notifications don't work.

### Gemfile

    gem 'growl'
    gem 'guard'
    gem 'guard-minitest'
    gem 'json'
    gem 'minitest'
    gem 'rack-test'
    gem 'ruby_gntp'
    gem 'sinatra'

### Guardfile

    guard :minitest do
watch(%r{^spec/(.*)_spec\.rb$})
watch(%r{^spec/test_helper.rb$})
watch('beacons_app.rb') { "spec/beacons_app_spec.rb" }
    end
    
    
    notification :gntp

(NOTE: I have tried putting the "notification" line at the top of the file as well)

If I run `bundle exec guard notifiers` gntp shows as available:

    +-------------------+-----------+------+--------+-------------+
| Name | Available | Used | Option | Value |
+-------------------+-----------+------+--------+-------------+
| gntp | ✔ | ✔ | title | "Notiffany" |
| | | | sticky | false |
+-------------------+-----------+------+--------+-------------+
| growl | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+
| terminal_notifier | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+
| libnotify | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+
| notifysend | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+
| notifu | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+
| emacs | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+
| tmux | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+
| terminal_title | ✔ | ✔ | title | "Notiffany" |
+-------------------+-----------+------+--------+-------------+
| file | ✘ | ✘ | | |
+-------------------+-----------+------+--------+-------------+

Growl is running and working (I can send to it successfully using `growlnotify` at the command line).

And when I run `bundle exec guard`, my tests run fine, and file changes trigger the tests to rerun in the terminal, as expected. But no growl notifications.

How can I make them work?

# UPDATE

This was caused by a bug in guard-minitest, and it has now been fixed: [https://github.com/guard/guard-minitest/commit/35ba44c2df7d25b8c3631be2571d3f1411e64185](https://github.com/guard/guard-minitest/commit/35ba44c2df7d25b8c3631be2571d3f1411e64185)


--------------------------------------- 
hmmm, my first guess would be that guard is not enabled in your growl settings:

have you checked your growl preferences?

![growl preferences](http://i.stack.imgur.com/2Gi4L.png)

I would also check [http://www.rubydoc.info/github/guard/guard/Guard/Notifier/Growl](http://www.rubydoc.info/github/guard/guard/Guard/Notifier/Growl)to ensure you have correct config options. if that doesn't work, open an issue at [https://github.com/guard/guard-minitest/issues](https://github.com/guard/guard-minitest/issues)

**Update: looks like this was a bug in guard-minitest** [https://github.com/guard/guard-minitest/issues/126](https://github.com/guard/guard-minitest/issues/126)


