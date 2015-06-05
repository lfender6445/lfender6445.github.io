---
layout: post
title: "change iterm2 profile based on session"
description: "change iterm2 profile based on session"
permalink: "iterm2-set-color-profile-based-on-session/"
category:
tags: ['terminal', 'shell']
---

it can be very useful to visually distinguish shell sessions based on type.

did you know you can change your terminal emulator profile for different connections? say for example, you're using ssh - you can wire up a quick function to change profiles on the fly:

{% highlight sh %}
# credit https://coderwall.com/p/s-2_nw/change-iterm2-color-profile-from-the-cli
# add this to your shell profile
set_iterm_profile() { echo -e "\033]50;SetProfile=$1\a" }
{% endhighlight %}

source your shell profile `source ~/.bash_profile`

now lets say you have 2 iterm profiles 'default' and 'deploy'

you can set up an alias to run `set_iterm_profile deploy` and your ssh command in sequence:

```
alias @deploy='set_iterm_profile deploy; ssh user@host; set_iterm_profile default;'
```

now your terminal emulator will set the new profile whenever you use the alias to connect to a box. when disconnecting, your profile will stitch back to your default :)

you'll end up with something like this:

![iterm session based profile](http://i.imgur.com/0vcioTN.png)

another option is to override the ssh method so it defaults to this behavior, but I prefer the simplicity of aliasing.


# some amazing iterm2 profile designs
iterm2 is a highly customizable terminal emulator for mac osx and ships with many options to tailor appearance.

check out [https://github.com/mbadolato/iTerm2-Color-Schemes](https://github.com/mbadolato/iTerm2-Color-Schemes) for some of the better designed terminal profiles out there.

# rainbow tab colors with iterm2
tab color can also be altered

![iterm2 colored tabs](http://i.imgur.com/lAMHLEJ.png?4)

iterm2 also lets you modify tab color to differentiate between sessions. check out my project [https://github.com/lfender6445/iterm2_rainbow_tabs](https://github.com/lfender6445/iterm2_rainbow_tabs) for randomized tab colors



