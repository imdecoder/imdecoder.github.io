---
title: "Poker StraightFlush"
date: 2017-09-02 00:51:22 +1000
guid: urn:uuid:9f5ac2af-8b45-4a55-bf4c-d6cc9fe34d8b
tags:
  - dev
  - algorithms
categories:
  - dev
external-url:
excerpt_separator: <!--more-->
---

First of all, PHP Code Example. (PHP ≥ 7)

    function isStriaghtFlush($d) {
        $b = $f = 0;
        $m = ['a'=>1,1=>10,'j'=>11,'q'=>12,'k'=>13];
        foreach ($d as $a) {
            $p = substr($a,-1);
            $b |= 1<<(($m[$a[0]])??$a[0]);
            $f = ($f===0||$f===$p) ? $p : 1;
        }
        $b = ($b << 3) | ($b >> 10);
        foreach (range(0,13) as $i) {
            if ((($b >> $i) & 31) == 31){
                return [true, $f!=1];
            }
        }
        return [false, false];
    }

<!--more-->

Explain:

`A` can be straight of `A, 2, 3, 4, 5` and `10, J, Q, K A`

There are total 14 ranks, when getting rank `n` from the `$d`, we set 1 of the `n` element in bitwise map.

If we could find any 5 continuously 1 in the bitwise map, then it’s straight. also if all faces are same, then it’s straight flush.

Example, cards: `10, J, Q, K, A`

read `10`, bitwise map: `0,0,0,1,0,0,0,0,0,0,0,0,0,0`

read `J`, bitwise map: `0,0,1,1,0,0,0,0,0,0,0,0,0,0`

read `Q`, bitwise map: `0,1,1,1,0,0,0,0,0,0,0,0,0,0`

read `K`, bitwise map: `1,1,1,1,0,0,0,0,0,0,0,0,0,0`

read `A`, bitwise map: `1,1,1,1,0,0,0,0,0,0,0,0,1,0`

shift left 3 of bitwise map to `1,1,1,1,0,0,0,0,0,0,0,0,1,0,0,0,0`

shift right 10 of bitwise map to `1,1,1,1`

OR this two bitwise maps and get a new map `1,1,1,1,0,0,0,0,0,0,0,0,1,1,1,1,1`

then we have 5 continuously 1, it’s straight.
