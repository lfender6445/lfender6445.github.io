---
layout: post
title: "nginx install on linux"
description: ""
category:
tags: []
---

nginx install on linux


I downloaded nginx from it's site for linux(I use ubuntu 10.4).I extracted nginx-1.0.6.tar.gz and there was a configure file in that directory. So I entered "./configure" command in shell. It seemed to be configured right.After I entered "make" command ,It said this error:

    make -f objs/Makefile
    make[1]: Entering directory `/usr/local/nginx'
    cd ./auto/lib/pcre/ \
  && if [-f Makefile]; then make distclean; fi \
  && CC="gcc" CFLAGS="-O2 -fomit-frame-pointer -pipe " \
  ./configure --disable-shared
    /bin/sh: ./configure: not found
    make[1]: *** [auto/lib/pcre//Makefile] Error 127
    make[1]: Leaving directory `/usr/local/nginx'
    make: *** [build] Error 2

what should I do now?


--------------------------------------- 
Enter your nginx install directory - I solved this error by editing objs/Makefile and removing -Wall and -Werror params so it looks like this (second line):

    CC = gcc
    CFLAGS = -pipe -O -W -Wpointer-arith -Wno-unused-parameter -Wunused-function -Wunused-variable -Wunused-value -g

Also, running your ./configure should initiate a long procedure of verifications to ensure that your system contains all the necessary components. If the configuration fails for any reason, check

    less objs/autoconf.err

for more details. Any errors at configuration are usually based on missing dependencies for your configuration.


