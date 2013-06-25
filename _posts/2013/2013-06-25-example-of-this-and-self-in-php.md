--- 
layout: post
title: "Example of $this and self:: in PHP"
date: 2013-06-25 11:27:13 +1000
guid: urn:uuid:f49f5955-ddcc-43c2-a031-65873301127e
tags:
  - php
  - dev
  - tips
categories:
  - dev
external-url: 
---
[source]: http://stackoverflow.com/questions/151969/when-to-use-self-vs-this

Saw this google example from [stackoverflow][source]

	class Person {
	    private $name;
	
	    public function __construct($name) {
	        $this->name = $name;
	    }
	
	    public function getName() {
	        return $this->name;
	    }
	
	    public function getTitle() {
	        return $this->getName()." the person";
	    }
	
	    public function sayHello() {
	        echo "Hello, I'm ".$this->getTitle()."<br/>";
	    }
	
	    public function sayGoodbye() {
	        echo "Goodbye from ".self::getTitle()."<br/>";
	    }
	}
	
	class Geek extends Person {
	    public function __construct($name) {
	        parent::__construct($name);
	    }
	
	    public function getTitle() {
	        return $this->getName()." the geek";
	    }
	}
	
	$geekObj = new Geek("Ludwig");
	$geekObj->sayHello();
	$geekObj->sayGoodbye();

Output:

	Hello, I'm Ludwig the geek
	Goodbye from Ludwig the person
	
`$this` will get function from object(extended class), but `self::` only get from current class