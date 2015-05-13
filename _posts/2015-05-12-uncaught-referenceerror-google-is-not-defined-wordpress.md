---
layout: post
title: "Uncaught ReferenceError: google is not defined (Wordpress)"
description: ""
category:
tags: []
---

Uncaught ReferenceError: google is not defined (Wordpress)


Below is the code I am working with. I'm trying to fix an error with a map not displaying in all browsers.

In dev tools (chrome), I'm getting a `Uncaught ReferenceError: google is not defined` error.

    $(document).ready(function(){
    
    
    //google map
    
    
    function loadGoogleMap() {
  var mapOptions = {
      scrollwheel: false,
      zoom: 14,
      mapTypeId: google.maps.MapTypeId.HYBRID
  };
  var map = new google.maps.Map($("#map")[0], mapOptions);
  var bounds = new google.maps.LatLngBounds();
    
    
  var count = 0;
  $.each(dealers, function(ind,dealer){
    
    
      var point = new google.maps.LatLng(dealer.lat,dealer.lng)
      var marker = new google.maps.Marker({
          position: point,
          map: map,
          title: dealer.post_title,
          icon: icons[count]
      });
      var infowindow = new google.maps.InfoWindow({
          content:'<div class="infowindow">'+
                      '<strong>' + dealer.post_title + '</strong><br/>' +
                      '<address>' +
                          dealer.address1 + '<br/>' +
                          dealer.city + ', ' + dealer.state + '<br/>' +
                      '</address>' +
                      dealer.phone + '<br/>' +
                      (dealer.url != '' ? '<a href="' + dealer.url+ '">Dealer Website</a><br/>' : '') +
                      (dealer.email != '' ? '<a href="mailto:' + dealer.email+ '">Email Dealer</a><br/>' : '') +
                      '<a href="http://maps.google.com/maps?f=d&source=s_d&saddr=&daddr=' + dealer.address + ', ' + dealer.city + ', ' + dealer.state + '" target="_blank">Get Directions</a>'+
                  '</div>'
      });
      google.maps.event.addListener(marker,'click',function(){
          infowindow.open(map,marker);
      });
    
    
      // add event listener to distributor list
      $('#distributors-list li:eq(' + count + ')').click(function(){
          infowindow.open(map,marker);
      });
    
    
      bounds.extend(point);
    
    
      count++;
  });
    
    
  map.fitBounds(bounds);
    }
    loadGoogleMap();
    
    
    // reuse fancybox loading icon script
    
    
    var loadingTimer, loadingFrame = 1;
    
    
    var locator_animate_loading = function() {
  locatorLoading = $('#ajax-loading-overlay');
  if (!locatorLoading.is(':visible')){
      clearInterval(loadingTimer);
      return;
  }
  $(locatorLoading).css('background-position', '0 ' + (loadingFrame * -40) + 'px');
    
    
  loadingFrame = (loadingFrame + 1) % 12;
    };
    
    
    $('form.distributor-search').submit(function(e){
  locatorLoading = $('#ajax-loading-overlay');
  locatorLoading.show();
  loadingTimer = setInterval(locator_animate_loading, 66);
  $('#locator-content').load(site_url + '/graceports/find-a-distributor?ajax=1&address=' + encodeURIComponent($('#address_search').val()) + ' #ajax-contents', function() {
      // load updated list of dealers
      $('#locator-content').append('<script src="' + site_url + '/js/dealers.php?address=' + encodeURIComponent($('#address_search').val()) + '"></script>');
      loadGoogleMap();
      locatorLoading.hide();
  });
  e.preventDefault();
    });
    
    
    navigator.geolocation.getCurrentPosition(function(position){
  $.get(site_url + '/cms/wp-content/themes/grace/inc/latlng-to-zip.php?latlng=' + encodeURIComponent(position.coords.latitude + ' ' + position.coords.longitude), function(data){
      $('#address_search').val(data);
      $('form.distributor-search').trigger('submit');
  });
    });
    
    
    });


--------------------------------------- 
You need to wait until google has loaded before running your scripts. Put this somewhere in your document:

    $(document).ready(function(){
    
    
    //google map
    
    
    
    
    
    
    function loadGoogleMap() {
  var mapOptions = {
      scrollwheel: false,
      zoom: 14,
      mapTypeId: google.maps.MapTypeId.HYBRID
  };
  var map = new google.maps.Map($("#map")[0], mapOptions);
  var bounds = new google.maps.LatLngBounds();
    
    
  function loadScript() {
  var script = document.createElement('script');
  script.type = 'text/javascript';
  script.src = 'https://maps.googleapis.com/maps/api/js?v=3.exp&' +
  'callback=initialize';
  document.body.appendChild(script);

}

    var count = 0;
  $.each(dealers, function(ind,dealer){
    
    
      var point = new google.maps.LatLng(dealer.lat,dealer.lng)
      var marker = new google.maps.Marker({
          position: point,
          map: map,
          title: dealer.post_title,
          icon: icons[count]
      });
      var infowindow = new google.maps.InfoWindow({
          content:'<div class="infowindow">'+
                      '<strong>' + dealer.post_title + '</strong><br/>' +
                      '<address>' +
                          dealer.address1 + '<br/>' +
                          dealer.city + ', ' + dealer.state + '<br/>' +
                      '</address>' +
                      dealer.phone + '<br/>' +
                      (dealer.url != '' ? '<a href="' + dealer.url+ '">Dealer Website</a><br/>' : '') +
                      (dealer.email != '' ? '<a href="mailto:' + dealer.email+ '">Email Dealer</a><br/>' : '') +
                      '<a href="http://maps.google.com/maps?f=d&source=s_d&saddr=&daddr=' + dealer.address + ', ' + dealer.city + ', ' + dealer.state + '" target="_blank">Get Directions</a>'+
                  '</div>'
      });
      google.maps.event.addListener(marker,'click',function(){
          infowindow.open(map,marker);
      });
    
    
      // add event listener to distributor list
      $('#distributors-list li:eq(' + count + ')').click(function(){
          infowindow.open(map,marker);
      });
    
    
      bounds.extend(point);
    
    
      count++;
  });
    
    
  map.fitBounds(bounds);
    }
    loadGoogleMap();
    
    
    // reuse fancybox loading icon script
    
    
    var loadingTimer, loadingFrame = 1;
    
    
    var locator_animate_loading = function() {
  locatorLoading = $('#ajax-loading-overlay');
  if (!locatorLoading.is(':visible')){
      clearInterval(loadingTimer);
      return;
  }
  $(locatorLoading).css('background-position', '0 ' + (loadingFrame * -40) + 'px');
    
    
  loadingFrame = (loadingFrame + 1) % 12;
    };
    
    
    $('form.distributor-search').submit(function(e){
  locatorLoading = $('#ajax-loading-overlay');
  locatorLoading.show();
  loadingTimer = setInterval(locator_animate_loading, 66);
  $('#locator-content').load(site_url + '/graceports/find-a-distributor?ajax=1&address=' + encodeURIComponent($('#address_search').val()) + ' #ajax-contents', function() {
      // load updated list of dealers
      $('#locator-content').append('<script src="' + site_url + '/js/dealers.php?address=' + encodeURIComponent($('#address_search').val()) + '"></script>');
      loadGoogleMap();
      locatorLoading.hide();
  });
  e.preventDefault();
    });
    
    
    navigator.geolocation.getCurrentPosition(function(position){
  $.get(site_url + '/cms/wp-content/themes/grace/inc/latlng-to-zip.php?latlng=' + encodeURIComponent(position.coords.latitude + ' ' + position.coords.longitude), function(data){
      $('#address_search').val(data);
      $('form.distributor-search').trigger('submit');
  });
    });

});


