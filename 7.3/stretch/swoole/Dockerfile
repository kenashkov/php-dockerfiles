FROM php:7.3-cli-stretch

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
        mysql-client \
	unixodbc-dev \
	procps \
	mc \
	wget \
	telnet \
	net-tools \
	screen \
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
    && pecl install swoole \
    && pecl install channel://pecl.php.net/mcrypt-1.0.2 \
    && pecl install mongodb \
    && pecl install sqlsrv \
    && pecl install pdo_sqlsrv \
    && pecl install inotify \
    && docker-php-ext-enable redis \
    && docker-php-ext-enable swoole \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-enable mongodb \
    && docker-php-ext-enable sqlsrv \
    && docker-php-ext-enable pdo_sqlsrv \
    && docker-php-ext-enable inotify


# install composer
RUN cd /root && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php ./composer-setup.php && cp ./composer.phar /usr/bin/composer && rm ./composer-setup.php