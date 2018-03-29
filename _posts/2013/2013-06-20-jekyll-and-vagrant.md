---
title: Jekyll and Vagrant
excerpt: ""
tags: [dev, vagrant, jekyll]
categories: dev
comments: true
guid: urn:uuid:ce55c8e0-d34c-4a24-8227-aebcbd057888
---

[1]: http://www.vagrantup.com/
Sometimes I want to run jekyll on office's computer which is using windows. I dont want to spend too much time to setup ruby or compile setup on windows, or even install linux on office's computer. [Vagrant][1] is a quick virtual machines to do the work!

Follow the instruction on vagrant website, and `vagrant init` in your project folder. Then open `Vagrantfile` to configure Vagrant

	Vagrant.configure("2") do |config|
		config.vm.box = "precise32"
		config.vm.network :forwarded_port, guest: 4000, host: 4000
		config.vm.provision :shell, :inline => "sudo apt-get update && sudo apt-get -y install build-essential ruby-compass && sudo /opt/vagrant_ruby/bin/gem install jekyll rdiscount --no-ri --no-rdoc"
	end

Then you are ready to start VM

	$vagrant up
	$vagrant ssh
	$cd /vagrant
	$jekyll server

After vagrant up successflly. You should be able to visit via http://localhost:4000 by your web browser.
