---
layout: post
title: "Joomla: pages not found after copying site to another directory"
description: ""
category:
tags: []
---

Joomla: pages not found after copying site to another directory


I have copied a live joomla site. The original is found at [this][1] website. The copied one in found [here][2]. But all links (e.g. in the left navigation menu) result in 404 errors. The administrator backend is accessible and i can create new menu items in the copied one but they all result in 404 errors.

I did adjust the configuration.php file so var $tmp\_path var $log\_path point the right paths. i updated var $live\_site = 'http://hosting01.hestronic.nl/~ijskoud2

The live\_site was empty in the original configuration.php file.

Do i still need to run an update or something?

Thank you

PS joomla 1.5.25


--------------------------------------- 
I ran into a similar issue where all of my links were doubling up. Fixed by prefixing `http://` to `$live_site`


