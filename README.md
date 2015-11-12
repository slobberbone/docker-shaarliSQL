# ShaarliSQL
[ShaarliSQL](http://git.gorgones.net/daniel.douat/shaarliSQL) is based on [Shaarli](http://sebsauvage.net/wiki/doku.php?id=php:shaarli).

ShaarliSQL, is a personal, minimalist, super-fast, with-database delicious clone.

## DockerHub repository
The images can be found in the [`slobberbone/docker-shaarlisql`](https://hub.docker.com/r/slobberbone/docker-shaarlisql/)
repository.

## Tags
Production:
- [`latest`](shaarli/README.md)

Development:
- [`dev`](shaarli-dev/README.md)

## Port

This image expose port 80.

## Volume

You can save your shaarliSQL directory by mapping them to the volume /var/www/html.

## Usage
```
docker run -d -v /*your_shaarli_location*:/var/www/html -p 8031:80 slobberbone/docker-shaarlisql  --link mysql-container:mysql
```
    
### Use Mysql link container

Some o environnement variable are shared with ShaarliSQL container, you can use it in the configuraiton screen (example):
MYSQL_PORT_3306_TCP_PORT=3306
MYSQL_PORT_3306_TCP=tcp://172.17.0.2:3306
MYSQL_PORT_3306_TCP_PROTO=tcp
MYSQL_NAME=/mysql-container/mysql
MYSQL_PORT_3306_TCP_ADDR=172.17.0.2
MYSQL_PORT=tcp://172.17.0.2:3306

## Nginx redirection for OMV

Create a configuration file in /etc/nginx/openmediavault-webgui.d/ named shaarli.conf wich contains :
```
  location /shaarli {
         proxy_pass         http://localhost:8031/shaarli;
         proxy_set_header   Host localhost:8031;
          proxy_redirect    default;
  }
```
Then reload nginx configuration :
```
service nginx reload
```
