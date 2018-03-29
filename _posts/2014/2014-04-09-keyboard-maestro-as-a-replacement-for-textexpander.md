---
title: Keyboard Maestro as a replacement for TextExpander
excerpt: ""
tags: [mac, app]
categories: mac
comments: true
guid: urn:uuid:e579d753-4c72-44fd-b2ff-e12e81517f1b
---

Recently, I started to try [Keyboard Maestro][km], and some people talked about it can be used as a replacement for [TextExpander][te].
Even I am not super fan of [TextExpander][te], but I still use it sometimes. I decided to try it to see difference.

###Trigger

Add a new trigger, select **Typed String Trigger**, then **This string is typed**.

Type any short string as trigger, eg. I use `gml  ` (two spaces after gml).
And other options which you can select as you like.

Make sure you tick `Simulaate x deletes before executing`,
otherwise the trigger phrase won't be deleted before expansion is inserted.

![Trigger](https://s3.amazonaws.com/f.cl.ly/items/0q0Y0D3t2K2D3l440L1f/keyboard-maestro-trigger.png?v=689c61e2)

###Actions

There are only two actions. One is **Insert Text**, and another is **Delete Past Clipboard**

**Insert Text** action, type the expansion into the textarea, and you also can use **Insert Token** to add variables of [Keyboard Maestro][te] given.

**Delete Past Clipboard** action, change the value to 0(default is 1), because **Insert Text** action will paste the expansion to clipboard, and replace any previously copied.

![Actions](https://s3.amazonaws.com/f.cl.ly/items/2g0w0w3L0y1k1Y0H1z2G/keyboard-maestro-actions.png?v=2c420e6a)

[km]: http://www.keyboardmaestro.com/
[te]: https://smilesoftware.com/TextExpander/
