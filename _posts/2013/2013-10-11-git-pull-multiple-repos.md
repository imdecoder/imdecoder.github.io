--- 
layout: post
title: "git pull multiple repositories"
date: 2013-10-11 12:30:21 +1100
guid: urn:uuid:29f2ea20-49ac-4862-870b-07cdcee8d35c
tags:
  - git
  - cmd
categories:
  - git
  - tips
external-url: 
---

	for REPO in `ls`; do (cd "$REPO";git pull); done;

