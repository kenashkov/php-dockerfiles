#Use PHP 7.4 docker image with Apache on Debian Stretch
FROM kenashkov/php:7.4.11-apache-stretch

EXPOSE 80
EXPOSE 9000

ENV DEPLOYMENT_IN_CONTAINER=true

#settigns needed by Apache to set the user/group under which it is running
#ENV APACHE_RUN_GROUP=#1000
#ENV APACHE_RUN_USER=#1000


# install some additional software and PHP extensions (both code and pecl ones)
# iconv, pdo, pdo_mysql are already available
#enable apache mod_rewrite
RUN apt-get update \
    && apt-get install -y mc wget netcat git libfreetype6-dev libjpeg62-turbo-dev libpng-dev libxml2-dev unixodbc-dev libmcrypt-dev gnupg inetutils-ping dnsutils telnet screen libzip-dev \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) bcmath \
    && docker-php-ext-install -j$(nproc) mysqli \
    && docker-php-ext-install -j$(nproc) soap \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && docker-php-ext-install -j$(nproc) opcache \
    && docker-php-ext-install -j$(nproc) calendar \
    && docker-php-ext-install -j$(nproc) zip \
    && docker-php-ext-install -j$(nproc) xml \
    && pecl install redis-4.3.0 \
    && pecl install mongodb \
    && pecl install xdebug \
#    && pecl install sqlsrv \
#    && pecl install pdo_sqlsrv \
    && pecl install stats-2.0.3 \
#    && pecl install mcrypt-1.0.2 \
    && docker-php-ext-enable redis \
    && docker-php-ext-enable mongodb \
    && docker-php-ext-enable xdebug \
#    && docker-php-ext-enable sqlsrv \
#    && docker-php-ext-enable pdo_sqlsrv \
    && docker-php-ext-enable stats \
#    && docker-php-ext-enable mcrypt \
    && a2enmod rewrite \
    && sed -i 's/AllowOverride None/AllowOverride All/g' /etc/apache2/apache2.conf \
    && sed -i 's/Options FollowSymLinks/Options Indexes MultiViews FollowSymLinks/g' /etc/apache2/apache2.conf \
    && sed -i 's/Options -Indexes/ /g' /etc/apache2/conf-available/docker-php.conf

# install gcloud
RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
   && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add - \
   && apt-get update -y && apt-get install -y google-cloud-sdk

# install composer
RUN cd /root && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php ./composer-setup.php && cp ./composer.phar /usr/bin/composer && rm ./composer-setup.php

# install psysh
RUN wget https://psysh.org/psysh \
   && chmod +x psysh \
   && mv ./psysh /usr/local/bin/psysh

# install phive
RUN wget -O phive.phar https://phar.io/releases/phive.phar \
   && chmod +x phive.phar \
   && mv phive.phar /usr/local/bin/phive

# install symfony
RUN wget https://get.symfony.com/cli/installer -O - | bash \
   && mv /root/.symfony/bin/symfony /usr/local/bin/symfony

#change the user id and group id of the www-data user and group to match the ones of the host
#we assume the user on the host that will be running the containers is 1000
# and change the DocumentRoot
RUN usermod -u 1000 www-data \
    && groupmod -g 1000 www-data \
    && mkdir /home/local \
    && chown www-data:www-data /home/local \
    && sed -i 's/\/var\/www\/html/\/home\/local/g' /etc/apache2/sites-available/000-default.conf \
    && sed -i 's/\/var\/www\//\/home\/local\//g' /etc/apache2/apache2.conf

WORKDIR "/home/local"


