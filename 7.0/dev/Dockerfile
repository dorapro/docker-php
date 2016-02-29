FROM dorapro/ubuntu:14.04

RUN apt-get update -q && apt-get install -yq --force-yes --no-install-recommends software-properties-common curl \
    && apt-add-repository ppa:ondrej/php -y \
    && apt-get update \
    && apt-get install -yq --force-yes --no-install-recommends \
       build-essential \
       curl \
       php7.0-cli \
       php7.0-dev \
       php-sqlite3 \
       php-gd \
       php-apcu \
       php-json \
       php-curl \
       php-gmp \
       php-imap \
       php-mbstring \
       php-mysql \
       php-memcached \
       php-readline \
       php-xdebug \
       php-xml \
       php-zip \
       php-intl
    && apt-get autoremove -qq \
    && apt-get clean -qq \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* >/dev/null 2>&1

RUN apt-get update -q && apt-add-repository ppa:git-core/ppa -y \
    && curl --silent --location https://deb.nodesource.com/setup_5.x | bash - \
    && apt-get install -yq --force-yes --no-install-recommends \
        git \
        openssh-client \
        php-xdebug \
        nodejs \
    && apt-get autoremove -qq \
    && apt-get clean -qq \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* >/dev/null 2>&1 \
    && mkdir -p ~/.ssh \
    && ssh-keyscan -H github.com >> ~/.ssh/known_hosts \
    && ssh-keyscan -H bitbucket.org >> ~/.ssh/known_hosts \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer self-update 1.0.0-alpha11 \
    && composer global require hirak/prestissimo \
    && curl -sS http://get.sensiolabs.org/php-cs-fixer.phar -o /usr/local/bin/php-cs-fixer \
    && chmod a+x /usr/local/bin/php-cs-fixer \
    && curl -sS https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar -o /usr/local/bin/phpcs \
    && chmod a+x /usr/local/bin/phpcs \
    && curl -sS https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar -o /usr/local/bin/phpcbf \
    && chmod a+x /usr/local/bin/phpcbf \
    && curl -sS http://static.phpmd.org/php/latest/phpmd.phar -o /usr/local/bin/phpmd \
    && chmod a+x /usr/local/bin/phpmd \
    && curl -sS https://github.com/phpmetrics/PhpMetrics/raw/master/build/phpmetrics.phar -o /usr/local/bin/phpmetrics \
    && chmod a+x /usr/local/bin/phpmetrics \
    && /usr/bin/npm install -gq gulp \
    && /usr/bin/npm install -gq bower

CMD ["php", "-a"]
