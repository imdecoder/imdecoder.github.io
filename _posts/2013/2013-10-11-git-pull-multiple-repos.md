---
title: Git pull multiple repositories
excerpt: ""
tags: [git]
categories: dev
comments: true
guid: urn:uuid:29f2ea20-49ac-4862-870b-07cdcee8d35c
---

~~~
for REPO in `ls`; do (cd "$REPO";git pull); done;
~~~
