---
layout: post
title: "Random 'concerns' folders and '.keep' files"
description: ""
category:
tags: []
---

Random 'concerns' folders and '.keep' files


I am learning rails.

Somewhere along the line, I noticed that seemingly random folders and files are appearing in my rails app's directory. In some folders there is a `concerns` folder with a `.keep` file inside it. The `.keep` file appears to be empty. In other folders there is no `concerns` folder but an empty `.keep` file is present.

Does anyone know what the deal with these files/folders is?


--------------------------------------- 
 **.keep files are especially helpful when you want to commit empty directories with git.**

The .keep files are there to prevent portage from one vcs to another, deleting important directories when you unmerge something that would cause those directories to be empty. It's a software design paradigm which seeks to decrease the number of decisions that developers need to make, gaining simplicity, but not necessarily losing flexibility.


