---

layout: post
title: A work-around for slow "git svn clone" on Windows
date: 2010-03-09 13:03:15 +01:00
permalink: /articles/152/a-work-around-for-slow-git-svn-clone-on-windows/
comments: true
categories: 
- Software-Entwicklung
---

There are a lot of reasons to use [git instead of svn](http://) . But it
is hard to switch to a new version control system in a running project.

[git-svn is a alternative](http://) if you would like to use git with an
existing subversion repository. Unfortunately `<code>`{=html}git svn
clone`</code>`{=html} is [dog slow on
windows](http://osdir.com/ml/version-control.msysgit/2008-05/msg00112.html)
. And I mean really slow. It would have taken more than 10 hours to
clone an existing project from the subversion repository. As this wasn't
an option I decided to do something which might be useful for other
purposes, too.

The unconventional solution:\
Run git-svn on Linux in virtual machine on Windows and copy it the
complete directory to windows.

Install VirtualBox\
http://www.virtualbox.org/wiki/Downloads

Download Ubuntu Image and unpack\
VirtualBoxes has some [ubuntu images ready to
run](http://virtualboxes.org/images/ubuntu/).

Configure Ubuntu VM in Virtualbox

Start Ubuntu

Configure shared folders\
`<code>`{=html}

1.  sudo mkdir /media/windows-share

<!-- -->

1.  sudo mount -t vboxsf folder-name /media/windows-share\
    `</code>`{=html}

Thanks to
[giannistsakiris.com](http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/)

Mount shared folder

Install git-core

Install git-svn

run git svn clone

copy directory to shared folder
