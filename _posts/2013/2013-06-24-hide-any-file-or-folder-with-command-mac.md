--- 
layout: post
title: "Hide Any File or Folder with Command"
date: 2013-06-24 11:01:42 +1000
guid: urn:uuid:aacb1361-a9ab-42cb-a857-e8a0f3d0ca03
tags:
  - mac
  - terminal
  - tips
categories:
  - mac
external-url: http://www.macobserver.com/tmo/article/os-x-hiding-items-with-the-terminal
---
Mac only

hide:

	chflags hidden /path/to/file-or-folder

unhide:

	chflags nohidden /path/to/file-or-folder

