FROM kenashkov/php:8.0.0-alpha-1-swoole-4.5.3-alpha-root

RUN groupadd -g 1000 dev \
    && useradd -u 1000 -g 1000 -m dev

COPY ./.bash_aliases /home/dev
COPY ./.bash_aliases/ /root


USER dev