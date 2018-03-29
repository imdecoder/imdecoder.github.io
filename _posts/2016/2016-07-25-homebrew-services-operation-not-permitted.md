---
title: "Homebrew Services Operation not permitted"
date: 2016-07-25 22:24:43 +1000
guid: urn:uuid:f24c29f5-e10e-4c5a-a449-e54fdfd3d909
tags:
  - dev
  - mac
categories:
  - mac
external-url:
show: excerpt
---

You will get this kind of error message when you run `brew services` in tmux

    /usr/local/Cellar/something/homebrew.mxcl.something.plist: Operation not permitted

How to fix it, just need install `reattach-to-user-namespace`

    brew install reattach-to-user-namespace
