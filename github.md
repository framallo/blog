---
layout: page
title: Github Projects
---


## Github profile

I have a lot of private repositories and applications I worked over the years. But also, I have some open source contributions. I'll try to summarise my open source code. But feel free to explore my [Github profile](https://github.com/framallo).

## Ruby and Rails

* [framallo/movies-with-neo4j](https://github.com/framallo/movies-with-neo4j) is a rails application using neo4j.rb and neo4j graph database. I've been doing research about graph databases. Currently, I'm a contributor of neo4jrb.
* [framallo/nomster](https://github.com/framallo/nomster) I am a mentor at [The firehose project](http://www.thefirehoseproject.com/), and this is a project assignment
* [framallo/geocoder_cli](https://github.com/framallo/geocoder_cli) I want to save addresses on my Garmin GPS. So I created this tool to get the GPS latitude and longitude of address.
* [framallo/torquebox](https://github.com/framallo/torquebox) I forked this project because I deployed a production application with JRuby. I wanted to use torque box features, but we couldn't implement torque box queues, so we had to move back to MRI Ruby. I realized at that moment that MRI Ruby was faster. This was back in 2012; probably things changed a lot.
* [framallo/bernard](https://github.com/framallo/bernard) is a personal finance application. I wrote it without tests, so now I'm coming back and writing the tests of the application.
* [framallo/excedent](https://github.com/framallo/excedent) is an application I build back in 2011 during a startup weekend

## Node

* [framallo/userver](https://github.com/framallo/userver) This is a toy node server I created.


## Vim

* [framallo/taskwarrior.vim](https://github.com/framallo/taskwarrior.vim) is a plugin that I created to use vim with task warrior

## Docker

I used docker to install [Tangosource](http://tangosource.com) as a multi tenance server. So production and staging are a docker instance each and, therefore, isolated from each other

* [tangosource/docker-php-fpm](https://github.com/tangosource/docker-php-fpm) is the base docker image
* [tangosource/docker-wordpress](https://github.com/tangosource/docker-wordpress) depends on docker-php-fpm and runs a wordpress server
* [tangosource/docker-nginx](https://github.com/tangosource/docker-nginx) runs an nginx server and connects with multiple wordpress instances


## Writing

* [framallo/blog](https://github.com/framallo/blog) is this blog
* [tangosource/innovation_articles PRIVATE](#) I created a wiki to manage articles from Tangosource developers

## Configuration files

* [gh-dotfiles](https://github.com/framallo/gh-dotfiles) Usually bash config files
* [framallo/Vim-for-Rails](https://github.com/framallo/Vim-for-Rails) I tried emacs and other editors, but I prefer Vim. I should refactor it and change some plugins
