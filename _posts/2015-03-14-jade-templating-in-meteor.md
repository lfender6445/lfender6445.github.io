---
layout: post
title: "Jade templating in Meteor"
description: ""
category:
tags: []
---

Jade templating in Meteor


In the Meteor FAQs [http://meteor.com/faq/how-do-i-package-a-new-templating-system](http://meteor.com/faq/how-do-i-package-a-new-templating-system) there is some information about adding a different (than the default Handlebars) templating system. Jade is the only other example explicitly called out elsewhere in the docs.

So is somebody already working on Jade? If not, is it feasible for me to start? Or is it still too early? e.g. :

> The package API is rapidly changing and isn't documented, so you can't make your own packages just yet. Coming soon.

I've been trying to love Handlebars in my current Ember.js project, but for me nothing is as elegant as Jade.


--------------------------------------- 
`mrt add jade`

in `client/views/templates/hello.jade` you could do something like this:

    template(name="hello")
h1 hello world!
{{greeting}}
    
    
input(type="button" value="click")

start you app with `mrt`


