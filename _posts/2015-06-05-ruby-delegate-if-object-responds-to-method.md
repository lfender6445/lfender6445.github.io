---
layout: post
title: "ruby delegate if object responds to method"
description: ""
permalink: "ruby-delegate-if-object-responds-to-method/"
tags: ['ruby']
---
I'd like to use delegation in Ruby, but I can't guarantee that the target object responds to all method I will call. May I define delegation with a default behaviour?

{% highlight ruby %}
class DummyPresenter
  delegate :name, :age, :to => :@content, :default => nil
  def initialize(content)
    @content = content
  end
end

class Student
  def name
    "name"
  end
end

DummyPresenter.new(Student.new).age # => nil
DummyPresenter.new(Student.new).name # => "name"
{% endhighlight %}

Now, the above example would raise:

    NoMethodError:
    undefined method `age' for #<Student:0xa121212>

---------------------------------------

I have found the easiest way to delegate methods to the original object is with SimpleDelegator (ships in stdlib)

{% highlight ruby %}
class Presenter < SimpleDelegator
  def initialize model
    super model
  end

  def foo
  'bar'
  end
end


class Person
  def bam
    'baz'
  end
end

person = Person.new
presenter = Presenter.new Person

presenter.foo # => 'bar'
presenter.bam # => 'baz'

{% endhighlight %}

From the docs:

> SimpleDelegator class provides the means to delegate all supported method calls to the object passed into the constructor
