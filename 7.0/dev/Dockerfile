FROM dorapro/php:7.0

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
    && ssh-keyscan -H github.com >> ~/.ssh/known_hosts \
    && ssh-keyscan -H bitbucket.org >> ~/.ssh/known_hosts \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer self-update 1.0.0-alpha11 \
    && curl -sS http://get.sensiolabs.org/php-cs-fixer.phar -o /usr/local/bin/php-cs-fixer \
    && chmod a+x /usr/local/bin/php-cs-fixer \
    && curl -sS https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar -o /usr/local/bin/phpcs \
    && chmod a+x /usr/local/bin/phpcs \
    && curl -sS https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar -o /usr/local/bin/phpcbf \
    && chmod a+x /usr/local/bin/phpcbf \
    && curl -sS http://static.phpmd.org/php/latest/phpmd.phar -o /usr/local/bin/phpmd \
    && chmod a+x /usr/local/bin/phpmd \
    && /usr/bin/npm install -gq gulp \
    && /usr/bin/npm install -gq bower

CMD ["php", "-a"]