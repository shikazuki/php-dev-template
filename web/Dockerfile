FROM php:7.0.22-apache

# add module required oss
RUN apt-get update && apt-get install -y zlib1g-dev libmcrypt-dev libicu-dev libxml2-dev libxslt1-dev libfreetype6-dev libjpeg62-turbo-dev libpng12-dev

RUN docker-php-ext-install -j$(nproc) fileinfo mbstring mysqli pdo_mysql zip soap mcrypt intl xsl

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-configure hash --with-mhash

RUN docker-php-ext-install -j$(nproc) gd hash

RUN apt-get install -y sendmail

# install composer
RUN cd /usr/local/bin && \
    curl -sS https://getcomposer.org/installer | php

RUN rm -rf /var/lib/apt/lists/* 

ADD mail.ini /usr/local/etc/php/conf.d/

RUN a2enmod rewrite

ENTRYPOINT ["docker-php-entrypoint"]
CMD ["apache2-foreground"]
