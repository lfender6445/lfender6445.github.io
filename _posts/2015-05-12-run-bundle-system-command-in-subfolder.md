---
layout: post
title: "Run `bundle` system command in subfolder"
description: ""
category:
tags: ['ruby']
permalink: "run-bundle-system-command-in-subfolder/"
---

Run `bundle` system command in subfolder


I am attempting to run `bundle` in a subfolder of my ruby project, but it appears to be running in the context of my initial directory even though I have changed the current working dir to the subfolder.

{% highlight ruby %}
# change directories and run bundle in a sub directory:
# ruby script.rb
system('bundle')
system('cd sub_folder')
system('bundle')
{% endhighlight %}

The bundle command runs successfully but only for the parent folder. Changing directories via system commands does not properly switch the context for bundler, and runs for the parent folders gemfile twice. What am I missing?


---------------------------------------
This can be fixed by changing bundlers context within your script:


{% highlight ruby %}
  Dir.chdir('sub_folder') do
    Bundler.with_clean_env do
      system('bundle')
    end
  end

{% endhighlight %}


More information on running bundler system commands via ruby:

  > Shelling out - Any Ruby code that opens a subshell (like system, backticks, or %x{}) will automatically use the current Bundler environment. If you need to shell out to a Ruby command that is not part of your current bundle, use the with\_clean\_env method with a block. Any subshells created inside the block will be given the environment present before Bundler was activated. For example, Homebrew commands run Ruby, but don't work inside a bundle:

  [http://bundler.io/man/bundle-exec.1.html#ENVIRONMENT-MODIFICATIONS](http://bundler.io/man/bundle-exec.1.html#ENVIRONMENT-MODIFICATIONS)


