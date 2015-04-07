---
layout: post
title: "What's the difference between to\_a and to\_ary in ActiveRecord?"
description: "difference beteen to_a and to_ary in active record"
category:
permalink: /difference-between-to_a-and-to_ary-in-active-record/
tags: ['ruby']
---

What's the difference between to\_a and to\_ary in ActiveRecord?

What's the difference between `ActiveRecord.to_a` and `ActiveRecord.to_ary`?

---------------------------------------
to\_a, when called on an object returns an array representation of obj

Examples

{% highlight ruby %}
class Example
  def initialize
    @str = 'example'
  end
end
a = Example.new #=> #<Example:0x105a74af8 @str="example"
a.to_a #=> [#<Example:0x105a6a3a0 @str="example">]
{% endhighlight %}

Hash Example

{% highlight ruby %}
h = { "c" => 300, "a" => 100, "d" => 400, "c" => 300 }
h.to_a #=> [["c", 300], ["a", 100], ["d", 400]]
{% endhighlight %}
> An array can also be created by using the Array() method, provided by Kernel, which tries to call to\_ary, then to\_a on its argument. [http://ruby-doc.org/core-2.0/Array.html#method-i-to\_ary](http://ruby-doc.org/core-2.0/Array.html#method-i-to_ary)

so as far as I can see, the Array#to\_ary src just returns the array that is passed in, as in

{% highlight ruby %}
def to_ary
  return self
end
{% endhighlight %}

if I understand correctly, to\_a is used for array conversion and makes its final return using to\_ary. But this may not be true in future versions according to apidock

> to\_a Returns an array representation of obj. For objects of class Object and others that don’t explicitly override the method, the return value is an array containing self. However, this latter behavior will soon be obsolete. [http://apidock.com/ruby/Object/to\_a](http://apidock.com/ruby/Object/to_a)
