---
layout: post
title: "a function to adjust spacing between paragraph to fill the div height"
description: ""
category:
tags: []
---

a function to adjust spacing between paragraph to fill the div height


What I have is a div with some items (menu item), this div will be the height of the browser viewer and I would like the spacing between the `<p>` to fill the height of the div.

So for a 1024px screen sixe, 20 px spacing is fine between paragraph, but sometimes it better to be 17px and for some big screen, 22 px should be fine.

Do you have a javascript function to auto calculate this or a jQuery plugin ?


--------------------------------------- 
If I understand you correctly, you are looking to modify the margin of p tags based on height of parent div - maybe something like this would help

    MAX = 200;
    if ($('div').height() > MAX) {
$('p').attr('style', 'margin:10px 0 10px 0;')
    } else {
$('p').attr('style', 'margin:0 0 0 0;')
    }


