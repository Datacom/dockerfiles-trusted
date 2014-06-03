## Base Ruby

This image designed to act as a multi-purpose base for ruby & rails containers
* Includes PPAs for Nginx, Redix, Nodejs
* Actually installs Nodejs and Nginx along with Ruby in the image
* making it ideal for static site deployment, particulary Jekyll based sites.


### Easy Shipping into non-internet accessible locations
`docker save datacom/base-ruby | gzip > base-ruby.tar.gz`
`docker load datacom/base-ruby < gunzip base-ruby.tar.gz`