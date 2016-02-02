---
layout: post
title: "Example of $this and self:: in PHP"
excerpt: ""
tags: [php]
categories: dev
comments: true
guid: urn:uuid:f49f5955-ddcc-43c2-a031-65873301127e
---

[source]: http://stackoverflow.com/questions/151969/when-to-use-self-vs-this

Saw this good example from [stackoverflow][source]

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
	
`$this` will refer to current object(extended class), but `self::` only refer to current class. If you want to refer to current object, you can use `static::` (>= PHP5.3.0)