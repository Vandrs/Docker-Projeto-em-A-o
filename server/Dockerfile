FROM php:5.6-apache

COPY ./conf/sites/* /etc/apache2/sites-available/
COPY ./conf/sites/* /etc/apache2/sites-enabled/
COPY ./conf/php/php.ini /usr/local/etc/php/php.ini

RUN apt-get update && apt-get install -y \
    libpq-dev \
    libmemcached-dev \
    curl \
    vim \
	nano \
    libjpeg-dev \
    libpng12-dev \
    libfreetype6-dev \
    libssl-dev \
    libmcrypt-dev \
	libxml2-dev \
    --no-install-recommends \
    && rm -r /var/lib/apt/lists/*

RUN docker-php-ext-install mcrypt 
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install pdo_pgsql
RUN docker-php-ext-install gd
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install soap
 
RUN curl -s http://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

RUN usermod -u 1000 www-data

CMD ["apache2-foreground"]

EXPOSE 80

