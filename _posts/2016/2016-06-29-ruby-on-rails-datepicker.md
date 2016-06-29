--- 
layout: post
title: "Ruby on Rails datepicker"
date: 2016-06-29 21:34:06 +1000
guid: urn:uuid:eefed055-5568-4939-8959-da20a9d041d7
tags:
  - dev
  - rails
categories:
  - dev
external-url: 
show: excerpt
---

Ruby on Rails datepicker

Use [bootstrap datepicker](https://github.com/Nerian/bootstrap-datepicker-rails) gem

Gemfile:

`gem 'bootstrap-datepicker-rails'`

Add this line to `app/assets/stylesheets/application.scss`

` *= require bootstrap-datepicker3`

Add this line to `app/assets/javascripts/application.js`

`//= require bootstrap-datepicker`

Add this line to template

`<%= f.text_field :publish_at, "data-provide" => 'datepicker', "data-date-format" => "yyyy-mm-dd" %>`


