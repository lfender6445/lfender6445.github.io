---
layout: post
title: "a smarter ls"
description: ""
category:
tags: ['shell', 'nix']
---

The `ls` command gets more action than I do. Find a file, view it, repeat. We can reduce this repetition by overriding the `ls` command that ships with your shell, and improve it a bit by displaying the contents of our newly found file.

```
function ls(){
  is_text=$(file $1|grep text)
  if [ $is_text ]; then
    less $1
  else
    ls $1
  fi
}
```

if its a text file, it will now be displayed.

save a keystroke, save a life.
