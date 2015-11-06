# docker-shaarliSQL
[![Docker repository](https://img.shields.io/docker/pulls/shaarli/shaarli.svg?style=plastic)](https://hub.docker.com/r/slobberbone/shaarliSQL/)

## ShaarliSQL
[ShaarliSQL](http://git.gorgones.net/daniel.douat/shaarliSQL) is based on [Shaarli](http://sebsauvage.net/wiki/doku.php?id=php:shaarli).

ShaarliSQL, is a personal, minimalist, super-fast, with-database delicious clone.


## DockerHub repository
The images can be found in the [`slobberbone/shaarliSQL`](https://hub.docker.com/r/slobberbone/shaarliSQL/)
repository.

## Tags
Production:
- [`latest`](shaarli/README.md)

Development:
- [`dev`](shaarli-dev/README.md)

## Docker usage
### Basics
Install [Docker](https://www.docker.com/), by following the instruction relevant
to your OS / distribution, and start the service.

### Run!
#### Get the ShaarliSQL image
    $ docker pull slobberbone/shaarliSQL


#### Create and start a new container from the image
    $ docker run -p 8000:80 slobberbone/shaarliSQL -v /a_directory:/var/www/html --link mysql-container:mysql
    
#### Use Mysql link container

Some o environnement variable are shared with ShaarliSQL container, you can use it in the configuraiton screen (example):
MYSQL_PORT_3306_TCP_PORT=3306
MYSQL_PORT_3306_TCP=tcp://172.17.0.2:3306
MYSQL_PORT_3306_TCP_PROTO=tcp
MYSQL_NAME=/mysql-container/mysql
MYSQL_PORT_3306_TCP_ADDR=172.17.0.2
MYSQL_PORT=tcp://172.17.0.2:3306

## Resources
### Docker
- [Dockerfile reference](https://docs.docker.com/reference/builder/)
- [Dockerfile best practices](https://docs.docker.com/articles/dockerfile_best-practices/)
- [Volumes](https://docs.docker.com/userguide/dockervolumes/)

### DockerHub
- [Repositories](https://docs.docker.com/userguide/dockerrepos/)
- [Teams and organizations](https://docs.docker.com/docker-hub/orgs/)
- [GitHub automated build](https://docs.docker.com/docker-hub/github/)

### Service management
- [Using supervisord](https://docs.docker.com/articles/using_supervisord/)
- [Nginx in the foreground](http://nginx.org/en/docs/ngx_core_module.html#daemon)
- [supervisord](http://supervisord.org/)

### Host configuration
- [Server requirements](https://github.com/shaarli/Shaarli/wiki/Server-requirements)
- [Server configuration](https://github.com/shaarli/Shaarli/wiki/Server-configuration)
- [Shaarli configuration](https://github.com/shaarli/Shaarli/wiki/Shaarli-configuration)
