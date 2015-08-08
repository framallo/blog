---
layout: post
title: Moving from rvm to rbenv
---

I am setting up this [blog](http://framallo.com), and I am setting up an AWS instance. You can check my setup [here](https://github.com/framallo/blog/tree/gh-pages/server_setup)

But turns out that [rvm](https://rvm.io/) installation is broken. It happens from time to time.  I used to use a workaround, and I can't find it right now. This is the error I've got:

{% highlight bash %}
    GPG signature verification failed for '/home/ubuntu/.rvm/archives/rvm-1.26.11.tgz' - 'https://github.com/rvm/rvm/releases/download/1.26.11/1.26.11.tar.gz.asc'!
    try downloading the signatures:
        gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
{% endhighlight %}

I don't want to deal with fixing it. I would rather try [rbenv](http://rbenv.org/). Specially after reading [RVM and rbenv](http://jonathan-jackson.net/rvm-and-rbenv) and [Why rbenv?](https://github.com/sstephenson/rbenv/wiki/Why-rbenv%3F)

I followed the steps in the documentation, and this is the commands that I run. Remember I'm using Ubuntu 14.04, so I need to change `~/.bash_profile` to `~/.profile`

    git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
    echo 'eval "$(rbenv init -)"' >> ~/.profile
    git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    source ~/.profile

Then I can install any version of ruby. In my case, I need ruby 2.1.2

    rbenv install 2.1.2
    rbenv rehash
    rbenv global 2.1.2


## Bad interpreter error

I found my first error! Yay!

    ubuntu@ip-172-30-0-171:~/blog$ bundle install
    -bash: /usr/local/bin/bundle: /usr/bin/ruby2.0: bad interpreter: No such file or directory

Turns out that, even though I uninstalled the ruby package, the bundler gem was still installed. So I had to do some cleanup

    sudo apt-get install ruby2.0
    sudo gem2.0 uninstall bundler
    sudo apt-get purge ruby2.0

## Summary 

Now, I can use Ruby 2.1.2 in Ubuntu 14.04. Happiness and joy!

