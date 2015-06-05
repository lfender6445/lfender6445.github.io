---
layout: post
title: "ruby searchkick failure : connection refused"
permalink: "ruby-searchkick-failure-connection-refused"
description: ""
category:
tags: ['ruby']
---

ruby searchkick failure : connection refused

I want to implement a searchkick on my Rails app, thus I my added to my gem file :

    gem 'elasticsearch'
    gem 'searchkick'

, did a

    bundle install

, and then

    rake searchkick:reindex CLASS=Pfile

It returns me the following error :

    rake aborted!
    No connection could be made because the target machine actively refused it. - connect(2)
    Tasks: TOP => searchkick:reindex
    (See full trace by running task with --trace)

---------------------------------------
ran into this myself. try `elasticsearch -f -D es.config=/usr/local/opt/elasticsearch/config/elasticsearch.yml`


