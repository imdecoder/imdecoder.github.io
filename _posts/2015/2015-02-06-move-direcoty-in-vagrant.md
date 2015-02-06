--- 
layout: post
title: "Vagrant: Move Project Directory"
date: 2015-02-06 10:58:04 +1100
guid: urn:uuid:aa7f724f-420d-4e79-8b18-5cd7ea175d28
tags:
  - dev
  - code
  - vagrant
categories:
  - dev
external-url: 
show: excerpt
---

[1]: https://laracasts.com/lessons/get-off-mamp-now
[2]: https://laracasts.com/
[3]: https://www.vagrantup.com/
[vaprobash]: https://github.com/fideloper/Vaprobash
[5]: https://docs.vagrantup.com/v2/synced-folders/nfs.html

I started to move my development works on my local envirnoment setup to [Vagrant][3]. Since I like to reinstall my system once major update released like Mac OSX 10.9 to 10.10, this will save lots of time for me.

And also, I watched this video [Get Off MAMP][1] on [Laracast][2] to push me move to [Vagrant][3].

Recently, I have moved one of my projects to a new directory, and it told me path is not correct once I `vagrant up` my project. Becuase I am using [Vaprobash][vaprobash] as basic start Vagrantfile, it is using [NFS][5] to sync folder between your local and box, which will modify `/etc/exports`.

What I need to do after I move existing project to another directory, I just need modify `/etc/exports` and update the directory path to new one.