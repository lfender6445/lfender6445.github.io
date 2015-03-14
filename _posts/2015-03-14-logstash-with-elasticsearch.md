---
layout: post
title: "Logstash with Elasticsearch"
description: ""
category:
tags: []
---

Logstash with Elasticsearch


I am trying to connect Logstash with Elasticsearch but cannot get it working.

Here is my logstash conf:

    input {
stdin {
  type => "stdin-type"
}
    
    
file {
  type => "syslog-ng"
    
    
  # Wildcards work, here :)
  path => ["/var/log/*.log", "/var/log/messages", "/var/log/syslog"]
}
    }
    
    
    output {
stdout { }
elasticsearch{
      type => "all"
      embedded => false
      host => "192.168.0.23"
      port => "9300"
      cluster => "logstash-cluster"
      node_name => "logstash"
      }
    }

And I only changed these details in my elasticsearch.yml

    cluster.name: logstash-cluster
    node.name: "logstash"
    node.master: false
    network.bind_host: 192.168.0.23
    network.publish_host: 192.168.0.23
    discovery.zen.ping.multicast.enabled: false
    discovery.zen.ping.unicast.hosts: ["localhost"]

With these configurations I could not make Logstash connect to ES. Can someone please suggest where I am going wrong?


--------------------------------------- 
This can also happen if your logstash + elasticsearch versions are out of sync

from the docs:

> VERSION NOTE: Your Elasticsearch cluster must be running Elasticsearch 1.1.1. If you use any other version of Elasticsearch, you should set protocol => http in this plugin.

Setting protocol explicitly did the trick for me.


