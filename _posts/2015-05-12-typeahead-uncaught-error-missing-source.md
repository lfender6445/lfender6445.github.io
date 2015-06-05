---
layout: post
title: "Typeahead: Uncaught Error Missing source"
description: ""
category:
tags: ["javascript"]
permalink: "typeahead-uncaught-error-missing-source/"
---

Typeahead: Uncaught Error Missing source

I am getting this error in console everytime I try to run the following code

{% highlight javascript %}
$('#autcomplete_search').typeahead({ highlight: true }, {
  name: 'apple_game',
  remote: "/search/autocomplete?keyword=make"
});
{% endhighlight %}

---------------------------------------
If fetching remote, you need to specify the engine. Here is an example from the docs

{% highlight javascript %}
var bestPictures = new Bloodhound({
  datumTokenizer: Bloodhound.tokenizers.obj.whitespace('value'),
  queryTokenizer: Bloodhound.tokenizers.whitespace,
  prefetch: '../data/films/post_1960.json',
  remote: '../data/films/queries/%QUERY.json'
});

bestPictures.initialize();

$('#remote .typeahead').typeahead(null, {
  name: 'best-pictures',
  displayKey: 'value',
  source: bestPictures.ttAdapter()
});
{% endhighlight %}

in this example, `bestPictures` is your engine
