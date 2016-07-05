--- 
layout: post
title: "Date Range Overlap"
date: 2016-07-05 21:37:43 +1000
guid: urn:uuid:ba48abab-b475-4eb2-b8d8-90f19febfcaa
tags:
  - dev
  - algorithms
categories:
  - dev
external-url: 
show: excerpt
---

# Date Range Overlap

Only 2  conditions that overlap does not exist
`                                                        |------ Date Range A ------|`
`|------ Date Range B ------|                                                        `

or

`|------ Date Range A ------|                                                        `
`                                                        |------ Date Range B ------|`

That means start date A is later than end date B, or end data A is early than start date B.

Overlap exists if neither of them is true.

In rails we can create a scope to find all overlaps 

```
scope :overlaps, -\>(start_date_, end_date_) do
  where “((start_date \<= ?) and (end_date \>= ?))", end_date_, start_date_ 
end
```

reference:
[http://stackoverflow.com/questions/325933/determine-whether-two-date-ranges-overlap](http://stackoverflow.com/questions/325933/determine-whether-two-date-ranges-overlap)
[http://baodad.blogspot.com.au/2014/06/date-range-overlap.html](http://baodad.blogspot.com.au/2014/06/date-range-overlap.html)