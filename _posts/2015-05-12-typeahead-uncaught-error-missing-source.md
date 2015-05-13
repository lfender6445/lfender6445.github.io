---
layout: post
title: "Typeahead: Uncaught Error Missing source"
description: ""
category:
tags: []
---

Typeahead: Uncaught Error Missing source


I am getting this error in console everytime I try to run the following code

    $('#autcomplete_search').typeahead({
highlight: true
    },
    {
name: 'apple_game',
remote: "/search/autocomplete?keyword=make"
    });


--------------------------------------- 
If fetching remote, you need to specify the engine. Here is an example from the docs

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

in this example, `bestPictures` is your engine


