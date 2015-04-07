---
layout: post
title: "Using data from one ajax request in another"
description: "Using data from one ajax request in another"
category:
permalink: /using-data-from-one-ajax-request-in-another/
tags: ['ajax']
---

Using data from one ajax request in another


I'm learning ruby but am going to need some JS/Jquery for a small project I'm working on with a friend. We're using the Last.fm api and are trying to build a page where we're going to call from two different URL's for Json data.

[http://ws.audioscrobbler.com/2.0/?method=user.getfriends&user=rj&api\_key=3d7e6bb560deeb5d15af8176abf5c928&format=json](http://ws.audioscrobbler.com/2.0/?method=user.getfriends&user=rj&api_key=3d7e6bb560deeb5d15af8176abf5c928&format=json)

Where we can pull out the friends username and some info about them, and

[http://ws.audioscrobbler.com/2.0/?method=user.gettoptracks&user=rj&period=7day&api\_key=3d7e6bb560deeb5d15af8176abf5c928&format=json](http://ws.audioscrobbler.com/2.0/?method=user.gettoptracks&user=rj&period=7day&api_key=3d7e6bb560deeb5d15af8176abf5c928&format=json)

where we can get the top tracks for each user.

The main problem I'm running in to is, once I pull out the username, I need to store it as a variable and then insert it inside the '&user=rj&' on get toptoptracks to be able to pull each users top tracks.

{% highlight javascript %}

$.ajax({
  type : 'POST',
  url : 'http://ws.audioscrobbler.com/2.0/?method=user.getfriends&user=rj&api_key=3d7e6bb560deeb5d15af8176abf5c928&format=json',
  dataType : 'json',
  success : function(data) {
      $('#success #f1').html(data.friends.user[0].name);
      $('#success #f2').html(data.friends.user[1].name);
      $('#success #f3').html(data.friends.user[2].name);
  },
  error : function(code, message){
      $('#error').html('Error Code: ' + code + ', Error Message: ' + message);
  }
});
{% endhighlight %}

is what I have so far (also one for toptracks, reading up on nesting them now), but I'm not sure how to get their user name AND store it as a variable to use inside the top tracks (.each do for JS?).

---------------------------------------

If I understand the problem correctly, something like this might help get you started:

{% highlight javascript %}

// at the top of your script create empty users var
var users = [];

// create a function that generates your endpoint url
var urlWithUser = function(user){
  return 'http://ws.audioscrobbler.com/2.0/?method=user.getfriends&user=' + user + '&api_key=3d7e6bb560deeb5d15af8176abf5c928&format=json'
};

// assign value to users
var getInitialData = function(){
  $.ajax({
    type : 'POST',
    url : 'http://ws.audioscrobbler.com/2.0/?method=user.getfriends&user=rj&api_key=3d7e6bb560deeb5d15af8176abf5c928&format=json',
    dataType : 'json',
    success : function(data) {
        users = data.friends.user;
        $.each(users, function(index, value){
            getUserData(this.name);
        };
    },
    error : function(code, message){
      $('#error').html('Error Code: ' + code + ', Error Message: ' + message);
    }
  });
};

// create a function with your ajax call, which can be used to obtain specific user data
var getUserData = function(user){
  $.ajax({
    type : 'POST',
    url : urlWithUser(user);
    dataType : 'json',
    success : function(data) {
      // do whatever you want
    },
    error : function(code, message){
      $('#error').html('Error Code: ' + code + ', Error Message: ' + message);
    }
  });
};

//get first set of users
getInitialData();
{% endhighlight %}

Note `urlWithUser` which accepts a user param and is used to generate specific endpoint for you.


