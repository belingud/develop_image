FROM php:7.2-fpm-alpine
ARG PHP_INI=/usr/local/etc/php/php.ini
ARG XDEBUG_INI=/usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
WORKDIR /tmp
ARG MIRROR=mirrors.tuna.tsinghua.edu.cn
ARG SOURCES="/etc/apk/repositories"
RUN sed -i 's/http/https/g' $SOURCES \
    && sed -i 's/dl-cdn.alpinelinux.org/'$MIRROR'/g' $SOURCES
RUN apk --no-cache add libpng libpng-dev ${PHPIZE_DEPS} \
    && docker-php-ext-install pdo pdo_mysql gd \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && echo 'xdebug.mode=debug' >> ${XDEBUG_INI} \
    && echo 'xdebug.idekey = PHPSTORM' >> ${XDEBUG_INI} \
    && echo 'xdebug.client_port=9003' >> ${XDEBUG_INI} \
    && echo 'xdebug.client_host=host.docker.internal' >> ${XDEBUG_INI} \
    && apk del ${PHPIZE_DEPS}
