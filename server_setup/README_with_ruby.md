
# install rvm 

    sudo apt-get install libxslt1.1 libxslt-dev xvfb build-essential git-core curl ruby libreadline6-dev zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 autoconf libgdbm-dev libncurses5-dev automake libtool bison pkg-config libffi-dev

    curl -L https://get.rvm.io | bash -s stable
    source ~/.rvm/scripts/rvm
    rvm install 2.2.2
    rvm use 2.2.2 --default
    gem install bundler

# Setup jekyll

