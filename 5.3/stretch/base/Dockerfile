FROM debian:stretch
# install basic tools and PHP dependencies

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
        build-essential \
        bison \
        re2c \
        libssl-dev \
        libcurl4-openssl-dev \
        pkg-config \
        libbz2-dev \
        libxpm-dev \
        libxpm4 \
        lemon \
        libtidy-dev \
        apt-utils \
        libxslt1.1 \
        libxslt1-dev

# install older openssl        
# https://www.openssl.org/source/old/0.9.x/openssl-0.9.8zh.tar.gz
# Installs to /usr/local/ssl/ (include located at /usr/local/ssl/include)
RUN cd /root \
    && wget "https://www.openssl.org/source/old/1.0.2/openssl-1.0.2u.tar.gz" \
    && tar -zxvf openssl-1.0.2u.tar.gz \
    && cd openssl-1.0.2u \
    && ./config \
    && make -j6 \
    && make install


# fix curl & libXpm
RUN cd /usr/include \
    && ln -s x86_64-linux-gnu/curl \
    && cd /usr/lib \
    && ln -s /usr/lib/x86_64-linux-gnu/libXpm.a
