FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN apt-get update -q && apt-get upgrade -yq --force-yes
RUN apt-get install -yq --force-yes --no-install-recommends software-properties-common \
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

CMD ["php", "-a"]
