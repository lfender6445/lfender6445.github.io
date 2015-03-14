---
layout: post
title: "How to set the Google Map zoom level to show all the markers?"
description: ""
category:
tags: []
---

How to set the Google Map zoom level to show all the markers?


How do I set the zoom level to show all the markers on Google Maps?

In my Google Map there are different markers in different positions. I want to set google map zoom level based on the range of markers (that means in the view of google map, i want to see all markers)


--------------------------------------- 
Maps API v3 --- get markers, set center on map by fitting map to marker boundaries

    markers = [marker_obj_1, marker_obj_2, marker_obj_3];
    
    
    new_boundary = new google.maps.LatLngBounds();
    
    
    for(index in markers){
position = markers[index].position;
new_boundary.extend(position);
    }
    
    
    map.fitBounds(new_boundary);

The code above will automaticlly center and zoom your map so that all markers are visible.


