# Image designed to act as a multi-purpose base for ruby & rails containers
# Includes PPAs for Nginx, Redix, Nodejs
# Actually installs Nodejs and Nginx along with Ruby in the image
# making it ideal for static site deployment, particulary Jekyll based sites.

FROM ubuntu:14.04
MAINTAINER Brad Murray <brad.murray@datacom.co.nz>

# Chris Lea's Nodejs, Rowan's Redis PPA, Stable Nginx
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C7917B12 &&\
    echo deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main > /etc/apt/sources.list.d/nodejs.list  &&\
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5862E31D &&\
    echo deb http://ppa.launchpad.net/rwky/redis/ubuntu trusty main > /etc/apt/sources.list.d/redis.list &&\
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C300EE8C &&\
    echo deb http://ppa.launchpad.net/nginx/stable/ubuntu trusty main > /etc/apt/sources.list.d/nginx.list

RUN apt-get update

RUN apt-get install -y --no-install-recommends \
    nano \
    curl \
    wget \
    git-core \
    ca-certificates \
    build-essential \
    nodejs \
    nginx && \
    apt-get clean && \
    rm -Rf /var/cache/*

# Ruby 2.1.2 stable via ruby-install, cleaned up the ruby src afterwards (src is 350mb)
RUN echo 'gem: --no-document' >> /usr/local/etc/gemrc &&\
    wget -O /tmp/ruby-install.tar.gz https://github.com/postmodern/ruby-install/archive/v0.4.3.tar.gz &&\
    tar -xzvf /tmp/ruby-install.tar.gz -C /opt && rm /tmp/ruby-install.tar.gz &&\
    /opt/ruby-install-0.4.3/bin/ruby-install -i /usr/local/ ruby 2.1.2 -- --disable-install-rdoc &&\
    echo 'Cleaning up Ruby src' &&\
    rm /usr/local/src/ruby-2.1.2.tar.bz2 &&\
    rm -rf /usr/local/src/ruby-2.1.2 &&\
    gem update --system &&\
    gem install bundler


