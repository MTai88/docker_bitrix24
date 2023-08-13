FROM bitrixdock/php56-fpm:latest

COPY ./php.ini /etc/php5/fpm/conf.d/90-php.ini
COPY ./php.ini /etc/php5/cli/conf.d/90-php.ini

#install mail
RUN apt-get update &&\
    apt-get install --no-install-recommends --assume-yes --quiet ca-certificates golang-go git &&\
    rm -rf /var/lib/apt/lists/*
RUN go install github.com/mailhog/mhsendmail@latest
RUN cp /root/go/bin/mhsendmail /usr/bin/mhsendmail

RUN usermod -u 1000 www-data

WORKDIR "/var/www/bitrix"

EXPOSE 9000
