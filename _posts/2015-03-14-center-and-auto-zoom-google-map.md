---
layout: post
title: "Center and auto zoom google map"
description: ""
category:
tags: []
---

Center and auto zoom google map


;)

I'm a not so familiar with the Google Maps API yet but I was able to figure out most questions a beginners faults. ;) But what I don't get is to center the map between the two markers I set and to auto zoom it... ;(

Maybe someone has the right hint for me...

Thanks and cheers!

    <script> function initialize() {
var myLatLng = new google.maps.LatLng(0, 0);
var mapOptions = {
  zoom: 3,
  mapTypeControl: false,
  navigationControl: false,
  scrollwheel: false,
  streetViewControl: false,
  zoomControl: false,
  center: myLatLng,
  mapTypeId: google.maps.MapTypeId.TERRAIN
};
    
    
var map = new google.maps.Map(document.getElementById('map'), mapOptions);
    
    
    
    
var flightPlanCoordinates = [
    new google.maps.LatLng(100, 100),
    new google.maps.LatLng(120, 120)
    
    
    
    
    
    
];
    
    
var lineSymbol = {
path: google.maps.SymbolPath.FORWARD_CLOSED_ARROW
    };
    
    
var flightPath = new google.maps.Polyline({
  path: flightPlanCoordinates,
  geodesic: true, 
  strokeColor: '#FF0000',
  strokeOpacity: 0.5,
  icons: [{
  icon: lineSymbol,
  offset: '100%'
}],
  strokeWeight: 2
});
    
    
flightPath.setMap(map);
    }
    
    
    google.maps.event.addDomListener(window, 'load', initialize);</script>

`<div id="map" style="width: 100%; height: 300px"></div>`

`<script>jQuery('#myModal-<? the_ID(); ?>').on('shown', function () {
  google.maps.event.trigger(map, 'resize');
  map.setCenter(new google.maps.LatLng(42.3605336, -72.6362989));
})</script>`


--------------------------------------- 
You need to fit the bounds of the map as it pertains to your markers.

    // Make an array of the LatLng's of the markers you want to show
    var LatLngList = new Array (new google.maps.LatLng (52.537,-2.061), new google.maps.LatLng (52.564,-2.017));
    // Create a new viewpoint bound
    var bounds = new google.maps.LatLngBounds ();
    // Go through each...
    for (var i = 0, LtLgLen = LatLngList.length; i < LtLgLen; i++) {
// And increase the bounds to take this point
bounds.extend (LatLngList[i]);
    }
    // Fit these bounds to the map
    map.fitBounds (bounds);


