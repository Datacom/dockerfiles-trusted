## Datacom Trusted Builds
Dockerfiles in here are for base layers to make projects easier.

### Easy Shipping into non-internet accessible locations
`docker save datacom/base-ruby | gzip > base-ruby.tar.gz`

`docker load datacom/base-ruby < gunzip base-ruby.tar.gz`