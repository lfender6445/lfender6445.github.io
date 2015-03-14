---
layout: post
title: "GMaps4Rails and Turbolinks not loading without full page refresh"
description: ""
category:
tags: []
---

GMaps4Rails and Turbolinks not loading without full page refresh


I'm using gmaps4rails to load a map on a "clients" show page. I've integrated turbolinks to make the app speadier all together, but now I'm hitting an issue where I have to refresh the page with the map for the map to show up. All I get is a blank map frame. When I refresh the page, the map shows up correctly.

I tried adding the gem 'jquery-turbolinks', but the problem persists.

In view:

    <%= gmaps("map_options" => {:container_class => "map_container_renamed", "zoom" => 15, "auto_zoom" => false},"markers" => { "data" => @json }) %>

In application.js

    //= require jquery
    //= require turbolinks
    //= require jquery.turbolinks
    //= require jquery_ujs
    //= require twitter/bootstrap
    //= require_tree .

Gist of page source where map is blank [here](https://gist.github.com/4254266).


--------------------------------------- 
I had trouble filling the map canvas on revisits to pages already managed by turbolinks, especially when using the back button. I fixed the issue by adding a listener, for the turbolinks event `page:load`, to map initialization.

**map.js.coffee**

    google.maps.event.addDomListener(window, 'load', @_setup)
    google.maps.event.addDomListener(window, 'page:load', @_setup)

**application.js.coffee**

    //= require jquery
    //= require jquery.turbolinks


