---
layout: post
title: "Determine if an Ad displayed and whether it was clicked"
description: ""
category:
tags: []
---

Determine if an Ad displayed and whether it was clicked


I am looking for information on how to implement something similar to the Facebook and Google advertising. I would like to have a folder with different images that are Ads for businesses and display them randomly on the page.

I want to keep track of how many times the Ad displayed and also whether or not it was clicked. I am not really sure where to start so I am hoping someone can point me in the right direction or give me a starting point. I wouldn't have a problem generating the random images but I'm afraid thats going to be the easiest part of this. Thanks in advance for any help!


--------------------------------------- 
I work for a high traffic website that tracks click behavior through a process called 'tagging'. Essentialy, whenever someone clicks on something, a 'tag' is fired.

**Whats happening behind the scenes** :

a javascript event is triggered, and a 1x1 transparent pixel object is downloaded to the users browser. The URL for this image contains a query string, housing important data relevant to the clicks location.

Example, a click on a high traffic website may trigger the download or request of an image with a `src` attribute that looks something like...

`tag.gif?page=productpage&coordinate_x=3478234&coordinate_y=342345&class=ad_container_4`.

The requests for the image are then logged and persisted into a database. The overhead for a 1x1 image is very small. When these requests are captured in logs, they can be used to aggregate data for behavioral analysis.

    requestURL = // http://url
    $('.ad').click(function(){firePixel();})
    firePixel = function(){
     tag = $('<img/>', {
        id: 'tag',
        border: '0',
        width: '1',
        height: '1',
        src: requestURL + '?class=' + classOfObjectClicked() + "&x_coord" + xCoordinate() _"&y_coord=" + yCoordinate()
      });
    }

just make sure that the image is publicly accessible.

This is one of many of many ways you can track clicks ^ \_ ^


