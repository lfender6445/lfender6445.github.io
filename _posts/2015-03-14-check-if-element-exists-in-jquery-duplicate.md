---
layout: post
title: "Check if element exists in jQuery [duplicate]"
description: ""
category:
tags: []
---

Check if element exists in jQuery [duplicate]


This question already has an answer here:

- [Is there an “exists” function for jQuery?](/questions/31044/is-there-an-exists-function-for-jquery) 20 answers 

How do I check if an element exists if the element is created by `.append()` method?`$('elemId').length` doesn't work for me.


--------------------------------------- 
I prefer

    if ($("#mydiv").length){ }

If it is 0, it will evaluate to `false`, anything more than that `true`.

No need for a greater than less than comparison.


