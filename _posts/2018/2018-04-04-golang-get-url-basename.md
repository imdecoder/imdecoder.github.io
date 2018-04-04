---
layout: single
title: "Get basename of url by Golang"
date: 2018-04-04 15:23:58 +1000
guid: urn:uuid:ee8f4525-e7cd-4721-bf12-d07c453beb9e
tags:
  - dev
  - golang
categories:
  - dev
external-url: 
feature: false
---

    targetURL := "http://www.example.com/one/two/three.json?output=four"
    u, err := url.Parse(targetURL)
    if err != nil {
      panic(err)
    }
    fmt.Println(path.Base(u.Path))
    // three.json