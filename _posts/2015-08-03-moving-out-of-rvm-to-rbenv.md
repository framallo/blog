---
layout: post
totle: Moving from rvm to rbenv
---

# Moving from rvm to rbenv

I am setting up this [blog](http://framallo.com) and I am setting up an aws instance. You can check my setup [here](https://github.com/framallo/blog/tree/gh-pages/server_setup)

But turns out that rvm instalation is broken. It happens from time to time.  I used to use a workaround and I can't find it right now. This is the error I've got:

    ubuntu@ip-172-30-0-171:~/blog$     curl -L https://get.rvm.io | bash -s stable
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100   184  100   184    0     0    454      0 --:--:-- --:--:-- --:--:--   454
    100 22721  100 22721    0     0  40246      0 --:--:-- --:--:-- --:--:--  172k
    Downloading https://github.com/rvm/rvm/archive/1.26.11.tar.gz
    Downloading https://github.com/rvm/rvm/releases/download/1.26.11/1.26.11.tar.gz.asc
    gpg: failed to create temporary file `/home/ubuntu/.gnupg/.#lk0xabc0b0.ip-172-30-0-171.1529': Permission denied
    gpg: keyblock resource `/home/ubuntu/.gnupg/pubring.gpg': general error
    gpg: Signature made Mon Mar 30 21:52:13 2015 UTC using RSA key ID BF04FF17
    gpg: Can't check signature: public key not found
    Warning, RVM 1.26.0 introduces signed releases and automated check of signatures when GPG software found.
    Assuming you trust Michal Papis import the mpapis public key (downloading the signatures).

    GPG signature verification failed for '/home/ubuntu/.rvm/archives/rvm-1.26.11.tgz' - 'https://github.com/rvm/rvm/releases/download/1.26.11/1.26.11.tar.gz.asc'!
    try downloading the signatures:

        gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3

    or if it fails:

        command curl -sSL https://rvm.io/mpapis.asc | gpg --import -

    the key can be compared with:

        https://rvm.io/mpapis.asc
        https://keybase.io/mpapis

I don't want to deal with fixing it. I would rather try [rbenv](http://rbenv.org/). Specially after reading [RVM and rbenv](http://jonathan-jackson.net/rvm-and-rbenv) and [Why rbenv?](https://github.com/sstephenson/rbenv/wiki/Why-rbenv%3F)

I followed the steps on the documentation and this is the commands that I run. Remember I'm using ubuntu 14.04, so I need to change `~/.bash_profile` to `~/.profile`

    git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
    echo 'eval "$(rbenv init -)"' >> ~/.profile
    git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    source ~/.profile

Then I can install any version of ruby. In my case I need ruby 2.1.2

    rbenv install 2.1.2
    rbenv rehash
    rbenv global 2.1.2

## Bad interpreter error

I found my first error! yay!

    ubuntu@ip-172-30-0-171:~/blog$ bundle install
    -bash: /usr/local/bin/bundle: /usr/bin/ruby2.0: bad interpreter: No such file or directory

Turns out that the bundler gem was still installed with `ruby2.0` ubuntu package. So I had to do some cleanup

    sudo apt-get install ruby2.0
    sudo gem2.0 uninstall bundler
    sudo apt-get purge ruby2.0
