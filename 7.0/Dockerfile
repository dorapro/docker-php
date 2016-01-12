FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN apt-get update -q && apt-get upgrade -yq --force-yes
RUN apt-get install -yq --force-yes --no-install-recommends software-properties-common curl \
    && apt-add-repository ppa:git-core/ppa -y \
    && apt-get install git -yq --force-yes --no-install-recommends \
    && apt-get autoremove -qq \
    && apt-get clean -qq \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* >/dev/null 2>&1

RUN apt-add-repository ppa:ondrej/php-7.0 -y \
    && curl --silent --location https://deb.nodesource.com/setup_5.x | bash - \
    && apt-get install -yq --force-yes --no-install-recommends \
       build-essential \
       openssh-client \
       nodejs \
       php7.0-cli \
       php7.0-dev \
       php7.0-readline \
       php-curl \
       php-gd \
       php-imap \
       php-intl \
       php-memcached \
       php-mysql \
       php-pgsql \
       php-sqlite3 \
       php-pear \
    && apt-get autoremove -qq \
    && apt-get clean -qq \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* >/dev/null 2>&1 \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer self-update 1.0.0-alpha11 \
    && /usr/bin/npm install -gq gulp \
    && /usr/bin/npm install -gq bower

CMD ["php", "-a"]
