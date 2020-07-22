FROM kenashkov/php:7.4.8-swoole-4.5.2-root

RUN groupadd -g 1000 dev \
    && useradd -u 1000 -g 1000 -m dev

COPY ./.bash_aliases /home/dev
COPY ./.bash_aliases/ /root


USER dev