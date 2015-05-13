---
layout: post
title: "ssh change default port"
description: "change default ssh port, mac or linux"
category:
tags: ['ssh']
permalink: 'ssh-change-default-port'
---

Working behind a firewall sucks - what if you need access to your remote linux instance?

With root access to your linux instance, you can easily change the default port for your connection:

```
sudo vim /etc/ssh/sshd_config
```

search for `Port` you will see it is commented out:

`#Port 22`

Uncomment it, and update to port number of your choice:

```
Port 222
```

then, restart ssh service __linux__

```
service sshd restart
```

__mac osx__ users can run the follow to restart ssh:

```
sudo launchctl stop com.openssh.sshd
```

and the service will restart on its own.

voila!  You can now connect to your box - just don't forget to specify the new port!

```
ssh user@host -p 222
```
