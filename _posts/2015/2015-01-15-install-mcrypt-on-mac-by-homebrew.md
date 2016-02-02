---
layout: post
title: Install Mcrypt on Mac by Homebrew
excerpt: ""
tags: [mac, php]
categories: dev
comments: true
guid: urn:uuid:2993b674-0fcc-46bc-a806-3267e3935587
---

Recently I setup Laravel enviroment on my Macbook, when I create project or run php artisan, it always prompts `Mcrypt PHP extension required.` error for me. Becuase I am using vagrant homestead for Laravel development, I can `homestead ssh` to run commands, but I think it’s better and convenience for me to install Mcrypt on my local enviroment. Then I did some reseach, and setup Mcrypt with mac native PHP.  

###There are three ways I found:

- Manually complie Mcrypt source and install
- Using Homebrew to install
- Using MAMP Mcrypt

For my requirement, I think homebrew is the best way for me.

###First
Install `autoconf` which is needed when homebrew compling Mcrypt

~~~
brew install autoconf
~~~

###Homebrew tap
Homebrew `dupes`, `versions`, and `homebrew-php` tap

~~~
brew tap homebrew/dupes
brew tap homebrew/versions
brew tap homebrew/homebrew-php
~~~

###Install `php55` or `php56`

~~~
brew install php55
~~~

or

~~~
brew install php56
~~~

###PHP Mcrypt

~~~
brew install php55-mcrypt
~~~

or

~~~
brew install php56-mcrypt
~~~

#Last
add mcrypt extension into `/etc/php.ini`. You can find path using `brew info php55-mcrypt`, eg.

~~~
extension= /usr/local/Cellar/php55-mcrypt/5.5.20/mcrypt.so
~~~




