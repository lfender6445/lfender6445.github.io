---
layout: post
title: "Ruby-Double quotes are missing when running shell script"
description: ""
category:
tags: []
permalink: "ruby-double-quotes-are-missing-when-running-shell-script"
---

Ruby-Double quotes are missing when running shell script

I have some json created from some data I send out and when I pass the json stored in a variable to another script ( created in python) I noticed that json elements are no longer double quotes

{% highlight ruby %}
json = @report.resultReportToJSON(result_type, result, unit)
puts "#{json}"
`"python ./post_request.py --json '#{json}'"`
{% endhighlight %}

My output is like this. From the puts it is :

    {"test_name":"Launch","requester":"foo","device_serial":"1234"}

and the command that gets executed ( we have some logging that outputs the command) is

    post_request.py --relative_path '/api/benchmark/' --json '{test_name:Launch,requester:foo,device_serial:1234}'

You can noticed the double quotes are gone

---------------------------------------
try this:

{% highlight ruby %}
require 'json'
`"python ./post_request.py --json '#{json.to_json}'"`
{% endhighlight %}

This will help to ensure the object is serialized with escaped quotes when translated to a system command.


