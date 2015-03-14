---
layout: post
title: "elasticsearch query to return all records"
description: ""
category:
tags: []
---

elasticsearch query to return all records


I have a small database in elasticsearch and for testing purposes would like to pull all records back. I am attempting to use a URL of the form...

    http://localhost:9200/foo/_search?pretty=true&q={'matchAll':{''}}

Can someone give me the URL you would use to accomplish this please?


--------------------------------------- 
`http://127.0.0.1:9200/foo/_search/?size=1000&pretty=1`

Note the size param, which increases the hits displayed from the default (10) to 1000.

[http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-request-from-size.html](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-request-from-size.html)


