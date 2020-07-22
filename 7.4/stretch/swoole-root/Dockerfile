FROM kenashkov/php:7.4.8-cli-stretch

# && docker-php-ext-install -j$(nproc) gettext \
# postgresql-client \
# && pecl install memcached \
# && docker-php-ext-enable memcached \

RUN cp /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libxml2 \
        libxml2-dev \
        libpq-dev \
        libmcrypt-dev \
        libonig-dev \
        libssl-dev \
        mysql-client \
        git \
	unixodbc-dev \
	procps \
	mc \
	wget \
	telnet \
	netcat \
	net-tools \
	screen \
	inetutils-ping \
	dnsutils \
	iproute2 \
	screen \
	tmux \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) bcmath \
    && docker-php-ext-install -j$(nproc) mbstring \
    && docker-php-ext-install -j$(nproc) soap \
    && docker-php-ext-install -j$(nproc) pgsql \
    && docker-php-ext-install -j$(nproc) mysqli \
    && docker-php-ext-install -j$(nproc) pdo \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && docker-php-ext-install -j$(nproc) pdo_pgsql \
    && docker-php-ext-install -j$(nproc) sockets \
    && docker-php-ext-install -j$(nproc) opcache \
    && docker-php-ext-install -j$(nproc) calendar \
    && docker-php-ext-install -j$(nproc) pcntl \
    && pecl install redis \
#    && pecl install swoole \
#    && pecl install channel://pecl.php.net/mcrypt-1.0.2 \
    && pecl install mongodb \
# sqlserv fails to compile on 7.4
#    && pecl install sqlsrv \
#    && pecl install pdo_sqlsrv \
    && pecl install inotify \
    && docker-php-ext-enable redis \
#    && docker-php-ext-enable swoole \
#    && docker-php-ext-enable mcrypt \
    && docker-php-ext-enable mongodb \
#    && docker-php-ext-enable sqlsrv \
#    && docker-php-ext-enable pdo_sqlsrv \
    && docker-php-ext-enable inotify


# install swoole Master
#RUN curl -fsSL 'https://github.com/swoole/swoole-src/archive/master.zip' -o swoole_master.zip \
#    && mkdir -p /tmp/swoole \
#    && unzip swoole_master.zip -d /tmp/swoole \
#    && rm swoole_master.zip \
#    && docker-php-ext-configure /tmp/swoole/swoole-src-master --enable-swoole --enable-http2 --enable-openssl \
#    && docker-php-ext-install -j$(nproc) /tmp/swoole/swoole-src-master \
#    && rm -r /tmp/swoole \
#    && docker-php-ext-enable swoole
    
# install swoole specific version
RUN curl -fsSL 'https://github.com/swoole/swoole-src/archive/v4.5.2.zip' -o swoole.zip \
    && mkdir -p /tmp/swoole \
    && unzip swoole.zip -d /tmp/swoole \
    && rm swoole.zip \
    && docker-php-ext-configure /tmp/swoole/swoole-src-4.5.2 --enable-swoole --enable-http2 --enable-openssl \
    && docker-php-ext-install -j$(nproc) /tmp/swoole/swoole-src-4.5.2 \
    && rm -r /tmp/swoole \
    && docker-php-ext-enable swoole
    
# install swoole_postgresql
#RUN curl -fsSL 'https://github.com/swoole/ext-postgresql/archive/master.zip' -o swoole_postgresql_master.zip \
#    && mkdir -p /tmp/swoole-postgresql \
#    && unzip swoole_postgresql_master.zip -d /tmp/swoole-postgresql \
#    && rm swoole_postgresql_master.zip \
#    && docker-php-ext-configure /tmp/swoole-postgresql/ext-postgresql-master --enable-swoole_postgresql \
#    && docker-php-ext-install -j$(nproc) /tmp/swoole-postgresql/ext-postgresql-master \
#    && rm -r /tmp/swoole-postgresql \
#    && docker-php-ext-enable swoole_postgresql
    

# install composer
RUN cd /root && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php ./composer-setup.php && cp ./composer.phar /usr/bin/composer && rm ./composer-setup.php


