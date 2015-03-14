---
layout: post
title: "How to remove/delete a large file from commit history in Git repository?"
description: ""
category:
tags: []
---

How to remove/delete a large file from commit history in Git repository?


Occasionally I dropped a DVD-rip into a website project, then carelessly `git commit -a -m ...`, and, zap, the repo was bloated by 2.2 gigs. Next time I made some edits, deleted the video file, and commited everything, but the compressed file is still there in the repository, in history.

I know I can start branches from those commits and rebase one branch onto another. But what should I do to merge together the 2 commits so that the big file didn't show in the history and were cleaned in garbage collection procedure?


--------------------------------------- 
I ran into this with a bitbucket account, where I had accidentally stored ginormous \*.jpa backups of my site.

`git filter-branch --prune-empty --index-filter 'git rm -rf --cached --ignore-unmatch MY-BIG-DIRECTORY-OR-FILE' --tag-name-filter cat -- --all`

Relpace `MY-BIG-DIRECTORY` with the folder in question to completely rewrite your history (_including tags_).

source: [http://naleid.com/blog/2012/01/17/finding-and-purging-big-files-from-git-history](http://naleid.com/blog/2012/01/17/finding-and-purging-big-files-from-git-history)


