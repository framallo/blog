# Setting up the server

I use amazon a t2.micro aws instance


# cold boot setup

    wget http://nginx.org/keys/nginx_signing.key > nginx_signing.key
    sudo apt-key add nginx_signing.key

    echo 'deb http://nginx.org/packages/debian/ codename nginx'     << /etc/apt/sources.list
    echo 'deb-src http://nginx.org/packages/debian/ codename nginx' << /etc/apt/sources.list
    sudo apt-get update
    sudo apt-get install nginx

    git clone https://github.com/framallo/blog.git
    cd blog
    sudo cp -f server_setup/nginx.conf /etc/nginx/sites-available/default

    sudo mkdir /var/www/
    sudo chown ubuntu:www-data /var/www
    sudo chmod 755 /var/www

     sudo service nginx restart

# ssh setup

I changed the ssh config file to run a shortcut. This is how `~/.ssh/config` looks like

    Host blog
      User           ubuntu
      HostName       <server host name>
      IdentityFile   <private key from aws>

# Production Deploy

You can deploy with this command

    rake deploy
