FROM php:7.2-fpm-buster
ARG PHP_INI=/usr/local/etc/php/php.ini
WORKDIR /tmp
RUN apt-get update && apt-get -y --no-install-recommends install libpng-dev \
    && docker-php-ext-install pdo pdo_mysql gd \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/Makefile.local > Makefile.local \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/config.m4 > config.m4 \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/php_xhprof.h > php_xhprof.h \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/trace.h > trace.h \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/config.w32 > config.w32 \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/xhprof.c > xhprof.c \
    && curl https://gitee.com/belingud/sources/raw/master/php.ini > ${PHP_INI} \
    && /usr/local/bin/phpize \
    && ./configure --with-php-config=$(which php-config) \
    && make && make install \
    && echo '[xhprof]' >> ${PHP_INI} \
    && echo 'extension = xhprof.so' >> ${PHP_INI} \
    && echo 'xhprof.output_dir = /var/log/xhprof' >> ${PHP_INI} \
    && rm -rf * 
