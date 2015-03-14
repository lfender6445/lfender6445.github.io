---
layout: post
title: "Javascript - ERR\_CONTENT\_LENGTH\_MISMATCH"
description: ""
category:
tags: []
---

Javascript - ERR\_CONTENT\_LENGTH\_MISMATCH


I'm making a basic jquery playground site. I am getting Error: `net::ERR_CONTENT_LENGTH_MISMATCH` is happening on page load and the background images are not loading on the page.

The image in question is 300kb and is also dynamically changing. I am assuming this has something to do with file sizes, but I dont really know what.

HTML used originally:

    <p style="margin:0px; padding:0px;"><img id="background" src="/bg1.jpg" style='width:100%;' border="0" alt="Null"></p>

javascript / jquery used to change the background:

    var changebg = function() {
  if (myscore % 20 == 0) {
      level++;
      document.getElementById("level").innerHTML = "Level: " + level;
      $("#level").fadeIn(1500, function(){$("#level").hide()})
      backgroundindex++;
      if (backgroundindex > 6) {backgroundindex == Math.floor((Math.random()*6)+1)};
    document.getElementById("background").src="/bg"+backgroundindex+".jpg";
  };
}


--------------------------------------- 
Have a look at your server logs to determine what the real issue is.

For me the problem lay somewhere between nginx and file permissions:

`tail -f /usr/local/var/log/nginx/error.log`

Refresh the asset in your browser, eg `http://localhost:3000/assets/jquery/jquery.js`

You may see something like this in the logs:

> "/usr/local/var/run/nginx/proxy\_temp/9/04/0000000049" failed (13: Permission denied) while reading upstream for file xyz

Heres how I fixed:

    sudo nginx -s stop
  sudo rm -rf /usr/local/var/run/nginx/*
  sudo nginx


