--- 
layout: post
title: "My Vagrant LAMP stack"
date: 2015-02-26 14:26:18 +1100
guid: urn:uuid:614f189a-01fe-4733-b06d-8e5d0321ab50
tags:
  - dev
  - vagrant
categories:
  - dev
external-url: 
show: excerpt
---

I was using [Vaprobash][vaprobash] as basic starting Vagranfile which is working perfectly '[post is here](/2015/02/05/move-direcoty-in-vagrant.html)'. However, there are too many settings I will never use, I think it's a better idea I make my own Vagranfile.

I vagranted up a new empty box, and run each commands to setup my LAMP environment, and recorded each command to shell scripts, that make sure all commands are just what I need.

Download my Vagrant LAMP:
**[My Vagrant LAMP][vagrant-lamp]**

TODO:
- remote call shell scripts like Vaprobash
- use puppet might be better

[vagrant-lamp]: https://github.com/imdecoder/vagrant-lamp
[vaprobash]: https://github.com/fideloper/Vaprobash