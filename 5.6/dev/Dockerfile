FROM dorapro/ubuntu:14.04

RUN apt-get update -q && apt-get install -yq --force-yes --no-install-recommends software-properties-common \
    && apt-add-repository ppa:ondrej/php5-5.6 -y \
    && apt-get update \
    && apt-get install -yq --force-yes --no-install-recommends \
       build-essential \
       curl \
       php5-apcu \
       php5-cli \
       php5-curl \
       php5-dev \
       php5-gd \
       php5-gmp \
       php5-imap \
       php5-intl \
       php5-json \
       php5-mcrypt \
       php5-memcached \
       php5-mysqlnd \
       php5-pgsql \
       php5-sqlite \
       php-pear \
    && apt-get autoremove -qq \
    && apt-get clean -qq \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* >/dev/null 2>&1

RUN apt-get update -q && apt-add-repository ppa:git-core/ppa -y \
    && curl --silent --location https://deb.nodesource.com/setup_5.x | bash - \
    && apt-get install -yq --force-yes --no-install-recommends \
        git \
        openssh-client \
        php5-xdebug \
        nodejs \
    && apt-get autoremove -qq \
    && apt-get clean -qq \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* >/dev/null 2>&1 \
    && mkdir -p ~/.ssh \
    && ssh-keyscan -H github.com >> ~/.ssh/known_hosts \
    && ssh-keyscan -H bitbucket.org >> ~/.ssh/known_hosts \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer self-update 1.1.1 \
    && composer global require hirak/prestissimo \
    && curl -sS http://get.sensiolabs.org/php-cs-fixer-v1.11.phar -o /usr/local/bin/php-cs-fixer \
    && chmod a+x /usr/local/bin/php-cs-fixer \
    && curl -sSL https://github.com/squizlabs/PHP_CodeSniffer/releases/download/2.5.1/phpcs.phar -o /usr/local/bin/phpcs \
    && chmod a+x /usr/local/bin/phpcs \
    && curl -sSL https://github.com/squizlabs/PHP_CodeSniffer/releases/download/2.5.1/phpcbf.phar -o /usr/local/bin/phpcbf \
    && chmod a+x /usr/local/bin/phpcbf \
    && curl -sS http://static.phpmd.org/php/latest/phpmd.phar -o /usr/local/bin/phpmd \
    && chmod a+x /usr/local/bin/phpmd \
    && /usr/bin/npm install -gq gulp \
    && /usr/bin/npm install -gq bower \
    && npm install -g eslint

CMD ["php", "-a"]
