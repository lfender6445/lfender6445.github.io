---
layout: post
title: "ruby block procs and method call"
permalink: "ruby-block-procs-and-method-call/"
description: ""
tags: ['ruby']
---

I'm trying to understand the need of the block `{ |s| puts s }` here:

{% highlight ruby%}
def accepts_hash( var )
  print "got: ", var.inspect # will print out what it received
end

accepts_hash( { :arg1 => 'giving arg1', :argN => 'giving argN' } ) { |s| puts s }
{% endhighlight %}

When I run this code, either with or without `{ |s| puts s }` ,

the output is still the same `({ :arg1 => 'giving arg1', :argN => 'giving argN' })`.

Can anyone please explain what does the block `{ |s| puts s }` do here?

(source: [http://en.wikibooks.org/wiki/Ruby\_Programming/Syntax/Method\_Calls](http://en.wikibooks.org/wiki/Ruby_Programming/Syntax/Method_Calls))


---------------------------------------
The block following your method call `{ |s| puts s }` does nothing until you tell it to. If you continue reading the page they explain blocks further down - here is an example:

{% highlight ruby%}
def accepts_hash( var )
  print "got: ", var.inspect # will print out what it received
  yield ' jenny from the block' # pass value back to block
end

accepts_hash( { :arg1 => 'giving arg1', :argN => 'giving argN' } ) { |s| puts s }
{% endhighlight %}

    => {:arg1=>"giving arg1", :argN=>"giving argN"} jenny from the block

By yielding, we can return and process the block - in this case `s` represents the string we are yielding, and `' jenny from the block'` is its value.

Blocks make ruby more flexible and declarative, allowing you to write idiomatic and human readable code. For example:

    3.times { p 'hello' }
    => "hello"
    => "hello"
    => "hello"

ruby is a gorgeous lanuage - more info on blocks and practical usage: [http://www.gotealeaf.com/blog/declarative-thinking-with-higher-order-functions-and-blocks](http://www.gotealeaf.com/blog/declarative-thinking-with-higher-order-functions-and-blocks)


