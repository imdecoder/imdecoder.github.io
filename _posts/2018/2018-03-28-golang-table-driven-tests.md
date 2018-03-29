---
title: "Table driven tests in Golang"
date: 2018-03-28 16:56:33 +1100
guid: urn:uuid:4038b9f6-7ad5-4556-9f1b-d1cbaba296e7
tags:
  - dev
  - go
  - test
categories:
  - dev
external-url: https://medium.com/@matryer/5-simple-tips-and-tricks-for-writing-unit-tests-in-golang-619653f90742
show: excerpt
---

```
var fibTests = []struct {
  n        int // input
  expected int // expected result
}{
  {1, 1},
  {2, 1},
  {3, 2},
  {4, 3},
  {5, 5},
  {6, 8},
  {7, 13},
}
```

source: https://medium.com/@matryer/5-simple-tips-and-tricks-for-writing-unit-tests-in-golang-619653f90742