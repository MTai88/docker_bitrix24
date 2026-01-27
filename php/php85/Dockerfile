FROM phpdockerio/php:8.5-fpm

RUN apt-get update \
    && apt-get -y --no-install-recommends install \
    php8.5-dev \
    php8.5-gd \
    php8.5-imagick \
    php8.5-intl \
    php8.5-interbase \
    php8.5-mbstring \
    php8.5-mcrypt \
    php8.5-memcache \
    php8.5-memcached \
    php8.5-mysql \
    php8.5-soap \
    php8.5-zip \
    php8.5-xdebug \
    ca-certificates golang-go git \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

COPY ./php.ini /etc/php/8.5/fpm/conf.d/90-php.ini
COPY ./php.ini /etc/php/8.5/cli/conf.d/90-php.ini

#install mail
RUN go install github.com/mailhog/mhsendmail@latest
RUN cp /root/go/bin/mhsendmail /usr/bin/mhsendmail

RUN if [ "$(id -u www-data)" != "1000" ]; then usermod -u 1000 -o www-data; fi

WORKDIR "/var/www/bitrix"

EXPOSE 9000
