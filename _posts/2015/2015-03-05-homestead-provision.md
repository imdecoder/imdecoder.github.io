--- 
layout: post
title: "Homestead provision"
date: 2015-03-05 14:02:59 +1100
guid: urn:uuid:1fff422a-1c45-4e55-8cc4-474ae6d9b75a
tags:
  - dev
  - homestead
  - vagrant
categories:
  - dev
external-url: 
show: excerpt
---

Laravel [Homestead][homestead] commands:

```
Available commands:
  destroy   Destroy the Homestead machine
  edit      Edit the Homestead.yaml file
  halt      Halt the Homestead machine
  help      Displays help for a command
  init      Create a stub Homestead.yaml file
  list      Lists commands
  resume    Resume the suspended Homestead machine
  run       Run commands through the Homestead machine via SSH
  ssh       Login to the Homestead machine via SSH
  status    Get the status of the Homestead machine
  suspend   Suspend the Homestead machine
  up        Start the Homestead machine
  update    Update the Homestead machine image
```

There is missing `provision` command

Solution is:

list all vagrant instance
```
$ vagrant global-status
id       name      provider   state    directory
-------------------------------------------------------------------------------------
6e1aa44  default   virtualbox poweroff /Users/[whoami]/.composer/vendor/laravel/homestead
```

then run provision with id
```
 $ vagrant provision 6e1aa4
 ```

[homestead]: https://github.com/laravel/homestead