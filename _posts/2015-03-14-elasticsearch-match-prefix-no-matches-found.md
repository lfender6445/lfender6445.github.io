---
layout: post
title: "Elasticsearch match prefix, no matches found"
description: ""
category:
tags: []
---

Elasticsearch match prefix, no matches found


Following an elastic search tutorial on some basic queries:

    #Create the index with no mapping
    curl -XPUT 127.0.0.1:9200/startswith/
    
    
    #add some data
    curl -XPOST 127.0.0.1:9200/startswith/test/ -d '{"title":"river dog"}'
    curl -XPOST 127.0.0.1:9200/startswith/test/ -d '{"title":"data"}'
    curl -XPOST 127.0.0.1:9200/startswith/test/ -d '{"title":"drive"}'
    curl -XPOST 127.0.0.1:9200/startswith/test/ -d '{"title":"dzone"}'
    
    
    #try to perform a "starts-with" style query...
    curl -XGET 127.0.0.1:9200/startswith/test/_search?pretty -d '{
      "query": {
      "match_phrase_prefix": {
         "title": {
           "query": "d",
           "max_expansions": 5
         }
       }
     }
   }' | grep title

but I am receiving the message `no matches found: 127.0.0.1:9200/startswith/test/_search?pretty`. If I visit `http://127.0.0.1:9200/startswith/test/_search` or curl it, the results are there. What am I missing?


--------------------------------------- 
I found the issue - sort of:

    curl -XGET 127.0.0.1:9200/startswith/test/_search?pretty -d '

What worked:

    curl -XGET '127.0.0.1:9200/startswith/test/_search?pretty' -d '

I needed quotes around the URL.

    $ curl -V
    curl 7.35.0 (x86_64-apple-darwin13.1.0) libcurl/7.35.0 SecureTransport zlib/1.2.5
    Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtsp smtp smtps telnet tftp
    Features: IPv6 Largefile NTLM NTLM_WB SSL libz

I've run the command in 2 different emulators. Quotes are required around the URL but I'm not really sure why. Bonus points for anyone who can tell me, as it doesn't appear to be required for the flag.

I am using `zsh`, not bash.


