---
layout: post
title: SSH Password for Windows Git bash
excerpt: ""
tags: [git]
categories: dev
comments: true
guid: urn:uuid:be54dc3f-cf5b-4ff4-98ee-3ea2ee26093c
---

I think it's more effective to use git cli than gui whatever which system you are using.

For example, you need switch branch, it's just one line in cli

> git checkout [branch]

But (eg. windows) you need right click -> choose command -> click -> choose branch -> click

It's ok if you just do this few times. However, if you like me, going to 10+ repositories and switch to different branches everyday. Command line is your best friend to help you save your time.

Terminal under Mac or *nix is native and easy to use. However, if you are using windows, after you install git, there is `git bash` to let you easy use git.

Then there is a problem, each time you push, pull, or commit, it requests you to type your ssh password.

What I did is every time when open a new terminal window, it will ask you your ssh password once, then whatever you do, it won't ask you password again until you close this seesion window.

Please find this file, if you could not find it, then create one.

> $HOME\\.bashrc

In this file, add below's code

~~~
eval `ssh-agent`
ssh-add
~~~

Now every time, when you open a new git bash window, it will your password once, and you can run as many commands as you want without popup to ask your password again.
