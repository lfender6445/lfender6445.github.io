---
layout: post
title: "Rails console with pry"
permalink: "rails-console-with-pry/"
description: ""
category:
tags: ['ruby']
---

I've set pry to load in place of irb when I enter rails console. I cannot find the page or remember how to bring it back to the default behavior as it seems to be interfering with my Rubymine debugger. Any suggestions?


---------------------------------------
You may have modified your `~/.irbrc` to start pry when IRB is loaded. Check there first.

Rails hooks into the application by loading your environment. To load your rails application into a pry session try this: `pry -I . -r config/environment`


