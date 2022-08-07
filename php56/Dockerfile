FROM bitrixdock/php56-fpm:latest

COPY ./php.ini /etc/php5/fpm/conf.d/90-php.ini
COPY ./php.ini /etc/php5/cli/conf.d/90-php.ini

#install mail
RUN apt-get update &&\
    apt-get install --no-install-recommends --assume-yes --quiet ca-certificates curl git &&\
    rm -rf /var/lib/apt/lists/*
RUN curl -Lsf 'https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz' | tar -C '/usr/local' -xvzf -
ENV PATH /usr/local/go/bin:$PATH
RUN go get github.com/mailhog/mhsendmail
RUN cp /root/go/bin/mhsendmail /usr/bin/mhsendmail

RUN usermod -u 1000 www-data

WORKDIR "/var/www/bitrix"

EXPOSE 9000
