---
title: Running Pow And MAMP Pro Together
excerpt: ""
tags: [mac, app, dev]
categories: dev
comments: true
guid: urn:uuid:b1e5ee85-72ab-4dcb-b714-5110acd040b1
---

[pow]: http://pow.cx
[mamp pro]: http://www.mamp.info

*source: [Running Pow with Apache](https://github.com/37signals/pow/wiki/Running-Pow-with-Apache)*

I use both [Pow][pow] for rails development and [MAMP Pro][mamp pro] for PHP development. I need them work simultaneously.

Before start, if you have [Pow][pow] installed, [uninstall](http://pow.cx/manual.html#section_1.2) it with

> curl get.pow.cx/uninstall.sh | sh

Then let pow's firewall run to redirect all traffic from port 88 instead of port 80

> echo 'export POW_DST_PORT=88' >> ~/.powconfig

Then you can [install](https://github.com/37signals/pow/wiki/Installation) [Pow][pow] as normal

> curl get.pow.cx | sh

Now, open [MAMP Pro][mamp pro], create a new host. Doesn't matter what it is named and which directory is selected (though I use 'rails.dev' and the folder I keep my Rails apps in).Also, deselect the select box for "local name resolution", just in case. Then go to the Advanced tab, and fill this in to the textarea labeled "Customized virtual host general settings":

    ServerName pow
    ServerAlias *.dev    

    ProxyPass / http://localhost:20559/
    ProxyPassReverse / http://localhost:20559/
    ProxyPreserveHost On