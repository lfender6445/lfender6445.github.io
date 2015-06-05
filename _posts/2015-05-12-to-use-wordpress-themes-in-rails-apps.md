---
layout: post
title: "To use Wordpress themes in Rails apps?"
description: ""
category:
tags: ['ruby', 'wordpress']
permalink: 'use-wordpress-themeses-in-rails-app/'
---

To use Wordpress themes in Rails apps?


Wordpress themes are beautiful!

Is there any guideline to use Wordpress themes in a rails app? Even better, are there rails app templates which can use the Wordpress themes already?

Thanks!


---------------------------------------
Did not find an easy solution to this so I created a gem, [theme_bandit](https://github.com/lfender6445/theme_bandit)

    gem install theme_bandit

It's a work in progress, but the gem allows you to build a tiny rack application out of an existing live site. If nothing else, this will do a large portion of the setup work when converting an existing template to a ruby project (handling of assets like js, css, and conversion for template engines)


