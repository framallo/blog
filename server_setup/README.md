# ssh setup

I changed the ssh config file to run a shortcut. This is how `~/.ssh/config` looks like

    Host blog
      User           ubuntu
      HostName       <server host name>
      IdentityFile   <private key from aws>

# setup production

You need to setup a git remote repository called production

    git remote add production blog:production

Then, you can deploy with a git push command

    git push production master

# setup staging

You need to setup a git remote repository called production

    git remote add staging blog:staging

Then, you can deploy with a git push command

    git push staging master


# Setting up the server

I use amazon a t2.micro aws instance


## cold boot setup

I should move this to a script, but usually is faster just to copy and paste to rebuild the instance.
I won't need to do it for a long time, but if I have to I would rather have detailed notes on how to rebuild

    # setup locale
    sudo echo 'export LANG=en_US.UTF-8'     >> /etc/default/locale
    sudo echo 'export LANGUAGE=en_US.UTF-8' >> /etc/default/locale
    sudo echo 'export LC_ALL=en_US.UTF-8'   >> /etc/default/locale

    # setup nginx
    wget http://nginx.org/keys/nginx_signing.key > nginx_signing.key
    sudo apt-key add nginx_signing.key
    echo 'deb http://nginx.org/packages/debian/ codename nginx'     << /etc/apt/sources.list
    echo 'deb-src http://nginx.org/packages/debian/ codename nginx' << /etc/apt/sources.list
    sudo apt-get update
    sudo apt-get install nginx

    sudo mkdir /var/www/production
    sudo mkdir /var/www/staging
    sudo chown -R ubuntu:www-data /var/www
    sudo chmod 755 /var/www

    # setup staging blog
    git clone https://github.com/framallo/blog.git staging
    cd staging

    # setup production blog
    git clone https://github.com/framallo/blog.git production
    cd production

    # setup nging config file
    sudo cp -f server_setup/nginx.conf /etc/nginx/sites-available/default
    
    # setup git hook
    ln -s ../../server_setup/post-receive .git/hooks/
    git config receive.denyCurrentBranch ignore

    sudo service nginx restart

    # setup rbenv
    git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
    echo 'eval "$(rbenv init -)"' >> ~/.profile
    git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

    source ~/.profile

    rbenv install 2.1.2
    rbenv rehash
    rbenv global 2.1.2

    gem install bundler

You server should be running
