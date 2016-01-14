FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_US.UTF-8
ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8

RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN apt-get update -q && apt-get upgrade -yq --force-yes
RUN apt-get install -yq --force-yes --no-install-recommends software-properties-common curl \
    && apt-add-repository ppa:ondrej/php-7.0 -y \
    && apt-get update \
    && apt-get install -yq --force-yes --no-install-recommends \
       build-essential \
       curl \
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
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* >/dev/null 2>&1

CMD ["php", "-a"]
