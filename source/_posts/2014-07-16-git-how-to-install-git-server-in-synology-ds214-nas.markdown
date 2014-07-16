---
layout: post
title: "Git - How to Install Git Server in Synology DS214 NAS?"
date: 2014-07-16 17:55:56 +0800
comments: true
categories: [Git, Synology, NAS, DS214]
keywords: Git, Synology, NAS, DS214
description: Git - How to Install Git Server in Synology DS214 NAS
---

Synology DS214 NAS is provided Git server package.

And I noted the setup below.

<!--more-->

Click Control Panel.
{% img /images/posts/2014-07-16-git/01.png %}

Create a new user account. (Example : git)
{% img /images/posts/2014-07-16-git/02.png %}
{% img /images/posts/2014-07-16-git/03.png %}

Create a new shared folder. (Example : Repository)
{% img /images/posts/2014-07-16-git/04.png %}

Select user git and on click Read/Write permission.
{% img /images/posts/2014-07-16-git/05.png %}

Click Package Center and install Git Server package.
{% img /images/posts/2014-07-16-git/06.png %}

Launch Git Server and allow user git to use.
{% img /images/posts/2014-07-16-git/07.png %}

Enable SSH srvices then save and reboot.
{% img /images/posts/2014-07-16-git/08.png %}

You need login NAS with root via ssh.
(Linux can use ssh command and Windows can use [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).)
```
$ ssh -l root 192.168.1.100 #192.168.1.100 is example. You need find your NAS local area IP.

$ Enter root password

$ cd /volume1/Repository/

$ mkdir moonlightbox.git

$ cd moonlightbox.git

$ git --bare init

$ cd ..

$ chown -R git:users moonlightbox.git

$ exit
```

Next, we will download moonlightbox project.
```
$ cd ~

$ git clone ssh://git@192.168.1.100/volume1/Repository/moonlightbox.git/

$ Enter git password # In this step, you can see the empty moonlightbox project.

$ cd moonlightbox

$ echo 1 > test.txt

$ git add .

$ git commit -m "Init test"

$ git push origin master

$ Enter git password # Finish check in "Init test" patch into git server.
```

HaHa. Done! :))))
