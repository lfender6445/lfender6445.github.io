---
layout: post
title: "How to change default root directory where PStore files are saved?"
description: ""
category:
tags: []
---

How to change default root directory where PStore files are saved?


I'm using PStore to persist some really basic information in a pretty standard way,

    @list_name = PStore.new(list_name)

How do you change the file location to not be root? I had a look around thru documentation but it seems to be pretty sparse

Thanks!


--------------------------------------- 
Just pass in the **path and name** on init

    # create
    @list_name = PStore.new('/tmp/wiki_pages.pstore')
    # persist
    @list_name.transaction {}

Look in tmp

    $ ls /tmp|grep wiki
    wiki_pages.pstore


