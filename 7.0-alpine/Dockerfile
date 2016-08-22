FROM php:7.0-fpm-alpine

RUN set -x \
    && apk add --no-cache --update freetype-dev icu-libs libjpeg-turbo-dev libpng-dev \
    && apk add --no-cache --virtual build-deps \
        ${PHPIZE_DEPS} \
        icu-dev \
    && docker-php-ext-configure gd \
        --with-png-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ \
        --with-freetype-dir=/usr/include/ \
    && docker-php-ext-install -j$(getconf _NPROCESSORS_ONLN) \
        ftp \
        gd \
        intl \
        opcache \
        pcntl \
        pdo \
        pdo_mysql \
        zip \
    && apk del --no-cache --purge build-deps \
    && mkdir -p /usr/src/php/ext

ENV PHP_AST_VERSION 0.1.2
RUN curl -fsSL "https://github.com/nikic/php-ast/archive/v${PHP_AST_VERSION}.zip" -o php-ast.zip \
    && unzip php-ast.zip -d /usr/src/php/ext \
    && mv /usr/src/php/ext/php-ast-${PHP_AST_VERSION} /usr/src/php/ext/php-ast \
    && rm php-ast.zip \
    && docker-php-ext-configure php-ast \
    && docker-php-ext-install -j$(getconf _NPROCESSORS_ONLN) php-ast \
    && mv /usr/local/etc/php/conf.d/docker-php-ext-ast.ini /usr/local/etc/php/conf.d/docker-php-ext-ast.ini.disabled

ENV XDEBUG_VERSION 2_4_1
RUN curl -fsSL "https://github.com/xdebug/xdebug/archive/XDEBUG_$XDEBUG_VERSION.zip" -o xdebug.zip \
    && unzip xdebug.zip -d /usr/src/php/ext \
    && mv /usr/src/php/ext/xdebug-XDEBUG_${XDEBUG_VERSION} /usr/src/php/ext/xdebug \
    && rm xdebug.zip \
    && docker-php-ext-configure xdebug \
    && docker-php-ext-install -j$(getconf _NPROCESSORS_ONLN) xdebug \
    && mv /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini.disabled
