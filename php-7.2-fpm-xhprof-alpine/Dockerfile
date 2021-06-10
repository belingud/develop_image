FROM php:7.2-fpm-alpine
WORKDIR /tmp
RUN docker-php-ext-install pdo pdo_mysql \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/Makefile.local > Makefile.local \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/config.m4 > config.m4 \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/php_xhprof.h > php_xhprof.h \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/trace.h > trace.h \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/config.w32 > config.w32 \
    && curl https://gitee.com/belingud/xhprof/raw/master/extension/xhprof.c > xhprof.c \
    && curl https://gitee.com/belingud/sources/raw/master/php.ini > /usr/local/etc/php.ini \
    && apk --no-cache add pcre-dev ${PHPIZE_DEPS} \
    && /usr/local/bin/phpize \
    && ./configure --with-php-config=$(which php-config) \
    && make && make install \
    && echo '[xhprof]' >> /usr/local/etc/php.ini \
    && echo 'extension = xhprof.so' >> /usr/local/etc/php.ini \
    && echo 'xhprof.output_dir = /var/log/xhprof' >> /usr/local/etc/php.ini \
    && rm -rf * && apk del pcre-dev ${PHPIZE_DEPS}
