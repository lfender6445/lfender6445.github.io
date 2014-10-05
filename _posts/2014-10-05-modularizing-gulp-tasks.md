---
layout: post
title: "modularizing gulp tasks"
description: "modularizing gulp tasks"
category:
tags: ['gulp', 'javascript']
permalink: /modularizing-gulp-tasks/
---

Gulp is nodes popular stream based building system, and has been an absolute pleasure to work with. However, as I move from project to project, I often find myself relying on the same tasks.

Whether its minification, or a set of release tasks, the game of copy and paste can be burdensome. No point in reinventing the wheel for a new project, right?

Thats when it struck me. Why not modularize the gulp tasks themselves? That way, I can just pull them into my current projects gulpfile.
modularizing gulp tasksr

## register gulp tasks via module.export

Node makes it relatively simple to require and scope methods to a single module. This post here on [StackOverflow](http://stackoverflow.com/questions/5797852/in-node-js-how-do-i-include-functions-from-my-other-files) shows that there are multiple ways to hammer a nail.

With gulp specifically, it is relatively easy to import tasks from another file. You do this simply by passing a reference to your initial `gulp` object.

{% highlight javascript %}
// add this to your gulpfile.js
var gulp = require('gulp');
// pass along gulp reference to import tasks onto your gulp object
require('gulp-foo')(gulp);
{% endhighlight %}

Node, by default, will look in our `node_modules` directory for a package with the name of gulp-foo

Inside of our module, we may expect to find something like this:

{% highlight javascript %}
// ./node_modules/gulp-foo/index.js
module.exports = function(gulp){
  gulp.task('foo', function(){
    console.log('foo');
  };
};
{% endhighlight %}

By running `gulp -T` will see that `foo` is now one of our registered tasks.

We can see that by only have 2 lines in our gulpfile, we've opened the door to task modularity and reuse.

## strive for modularity with gulp
I am sick to death of writing the same coffee in coffee out task from project to project. It can prove to be pretty monotomnous.

We all have different ways of doing things in our projects, especially with gulp.

Some of us may keep our coffee in a separate folder than our javascripts, some of us may not.

 __But if you think you've written a pretty good gulp task, and your proud of it, why not register it on npm? share it with the world__

that way the rest of us can stop wasting time putting together our own gulp tasks, we can standardize our projects, and focus on what we love most.

## gulp release tasks, a real world example

I've applied this concept in a project called [gulp release tasks](https://github.com/lfender6445/gulp-release-tasks) which I hope proves useful to gulp, npm, and bower lovers alike.

