---
title: "MariaDB failed to start"
date: 2016-12-27 19:16:36 +1100
guid: urn:uuid:9a65b212-796d-4b90-ab34-1554f7eae499
tags:
  - dev
categories:
  - dev
external-url:
show: excerpt
---

Using Homebrew to install MariaDB, and got this eror when starting the server

    $ mysql.server start
    Starting MySQL
    .161227 19:05:10 mysqld_safe Logging to '/usr/local/var/mysql/xxx.err'.
    ERROR!

Mostly it is caused by previous installation of MySQL.

Manually remove `/usr/local/var/mysql` and reinstall MariaDB,
it will start normally.
