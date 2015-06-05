---
layout: post
title: "Rails order by with associated model"
permalink: "rails-order-by-with-associated-model/"
description: ""
category:
tags: ['ruby']
---

I have two models in a has\_many relationship such that Log has\_many Items. Rails then nicely sets up things like: `some_log.items` which returns all of the associated items to some\_log. If I wanted to order these items based on a different field in the Items model is there a way to do this through a similar construct, or does one have to break down into something like:

    Item.find_by_log_id(:all,some_log.id => "some_col DESC")


---------------------------------------
 **rails 4.2.20** syntax requires calling with a block:


{% highlight ruby %}
    class Item < ActiveRecord::Base
      default_scope { order('some_col DESC') }
    end
{% endhighlight %}

This can also be written with an alternate syntax:

{% highlight ruby %}
  default_scope { order(some_col: :desc) }
{% endhighlight %}

