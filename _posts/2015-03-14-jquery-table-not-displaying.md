---
layout: post
title: "Jquery table not displaying"
description: ""
category:
tags: []
---

Jquery table not displaying


I am trying to use code that works in an onclick function of a button in an href click, but it is not displaying.

I am trying to hide the searchTable and display the new table, but can't figure out what I am doing wrong.

[My Fiddle](http://jsfiddle.net/CLqdz/1/)

    $("#searchTable").hide();
    
    
    var table = $('<table />').attr({
                "id": "searchTableResult",
                "width": "75%",
                "border": "1",
                "cellpadding": "0",
                "cellspacing": "0"
              });
    
    
              thead = $('<thead />'),
              tbody = $('<tbody />'),
              tr = $('<tr />'),
              th = $('<th />'),
              td = $('<td />');
              a = $('<a />').attr({
                "class": "set-url",
                "href": "#"
              });
          thead.append( // append a new row to thead
              tr.clone()
                  .append(th.clone().text('Name')) // populate th with labels
                  .append(th.clone().text('Set'))
  );           
    
    
    
    
  });


--------------------------------------- 
don't forget to append the thead to the table and the table to the DOM

    $('body').append(table.append(thead));

It looks like you've created a table var but never even use it.


