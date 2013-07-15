--- 
layout: post
title: "JSONP and JSON"
date: 2013-07-15 16:38:33 +1000
guid: urn:uuid:37d7de07-2613-47e7-a73c-48d999fbe4db
tags:
  - dev
  - php
categories:
  - dev
external-url: 
---

[1]: http://stackoverflow.com/questions/2887209/what-are-the-differences-between-json-and-jsonp
[2]: https://gist.github.com/cowboy/1200708

Let's see what's differences between JSON and JSONP first;

	//JSON
	{"name":"stackoverflow","id":5}
	//JSONP
	func({"name":"stackoverflow","id":5});
	
JSONP is the result that you can load the json as a script file. And it is usually used to allow for cross-site AJAX with JSON data.

	function func(json){
	  alert(json.name);
	}
	var elm = document.createElement("script");
	elm.setAttribute("type", "text/javascript");
	elm.src = "http://example.com/jsonp";
	document.body.appendChild(elm);
	
Convert JSON to JSONP in PHP, JSONP will pass `callback` to script

	$json = json_encode($data);
	$jsonp_callback = isset($_GET['callback']) ? $_GET['callback'] : null;
	echo $jsonp_callback ? "$jsonp_callback($json)" : $json;
	

Rerference: [Stack Overflow][1]