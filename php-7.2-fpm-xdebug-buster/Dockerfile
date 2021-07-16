FROM php:7.2-fpm-buster
ARG PHP_INI=/usr/local/etc/php/php.ini
ARG XDEBUG_INI=/usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
WORKDIR /tmp
RUN apt-get update && apt-get -y --no-install-recommends install libpng-dev \
    && docker-php-ext-install pdo pdo_mysql gd \
    && curl https://gitee.com/belingud/sources/raw/master/php.ini > ${PHP_INI} \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    # && echo 'zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20170718/xdebug.so' >> ${XDEBUG_INI} \
    && echo 'xdebug.mode=debug' >> ${XDEBUG_INI} \
    && echo 'xdebug.idekey = PHPSTORM' >> ${XDEBUG_INI} \
    && echo 'xdebug.client_port=9003' >> ${XDEBUG_INI} \
    && echo 'xdebug.client_host=host.docker.internal' >> ${XDEBUG_INI}
