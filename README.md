# Docker images for PHP

The images are based on the official PHP images and dockerfiles.

The following tags are available:
- [7.4-apache-stretch](https://github.com/kenashkov/php-dockerfiles/blob/master/7.4/stretch/apache/Dockerfile) - RC4 - build by using the [Dockerfile for PHP 7.3](https://github.com/docker-library/php/blob/3a546766fdeb873090c7e87c4ec3491841bafb1c/7.3/stretch/apache/Dockerfile) with minor tweaks.
- [7.4-apache-stretch-dev](https://github.com/kenashkov/php-dockerfiles/blob/master/7.4/stretch/apache-dev/Dockerfile) - PHP 7.4 RC4, mongodb, redis, mcrypt, stats, gd, bcmath, mysqli, pdo_mysql, soap, opcache, calendar, zip
- [7.4-cli-stretch](https://github.com/kenashkov/php-dockerfiles/blob/master/7.4/stretch/cli/Dockerfile) - PHP 7.4 RC4
- [7.4-swoole-stretch](https://github.com/kenashkov/php-dockerfiles/blob/master/7.4/stretch/swoole/Dockerfile) - PHP 7.4 RC4, swoole 4.4.9-alpha, swoole_postgresql, Swoole HTTP2 and HTTPS enabled
- [7.3-swoole-stretch](https://github.com/kenashkov/php-dockerfiles/blob/master/7.3/stretch/swoole/Dockerfile) - PHP 7.3.10, swoole 4.4.9-alpha, swoole_postgresql, Swoole HTTP2 and HTTPS enabled
