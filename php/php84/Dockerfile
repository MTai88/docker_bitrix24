FROM phpdockerio/php:8.4-fpm

RUN apt-get update \
    && apt-get -y --no-install-recommends install \
    php8.4-dev \
    php8.4-gd \
    php8.4-imagick \
    php8.4-intl \
    php8.4-interbase \
    php8.4-mbstring \
    php8.4-mcrypt \
    php8.4-memcache \
    php8.4-memcached \
    php8.4-mysql \
    php8.4-opcache \
    php8.4-soap \
    php8.4-zip \
    php8.4-xdebug \
    ca-certificates golang-go git \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

COPY ./php.ini /etc/php/8.4/fpm/conf.d/90-php.ini
COPY ./php.ini /etc/php/8.4/cli/conf.d/90-php.ini

#install mail
RUN go install github.com/mailhog/mhsendmail@latest
RUN cp /root/go/bin/mhsendmail /usr/bin/mhsendmail

RUN if [ "$(id -u www-data)" != "1000" ]; then usermod -u 1000 -o www-data; fi

WORKDIR "/var/www/bitrix"

EXPOSE 9000
