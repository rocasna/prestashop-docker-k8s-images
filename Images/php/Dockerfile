FROM php:7.4.32-fpm

RUN apt-get update \
    && apt-get install -y wget curl nano \
    && apt-get install -y --no-install-recommends \
			   libpng-dev \
			   libzip-dev \
			   libicu-dev \
			   libzip4 \
			   libfreetype6-dev \
        	   libjpeg62-turbo-dev \
			   libmcrypt-dev \
			   zlib1g-dev \
			   libxml2-dev \
			   libonig-dev \
			   graphviz \
			   libz-dev libmemcached-dev \
	&& pecl install xdebug \
	&& docker-php-ext-install opcache \
    && docker-php-ext-enable xdebug \
    && apt-get install -y \
	&& docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install exif \
	&& docker-php-ext-install zip \
	&& docker-php-ext-install gd \
	&& docker-php-ext-install intl \
	&& docker-php-ext-install bcmath \
	&& docker-php-ext-install mysqli \
	&& pecl install memcached \
    && docker-php-ext-enable memcached \
    && apt-get install -y libmagickwand-dev --no-install-recommends \
	&& pecl install imagick \
    && docker-php-ext-enable imagick

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

COPY php.ini /usr/local/etc/php/

RUN rm -rf /etc/localtime \
        && ln -s /usr/share/zoneinfo/Europe/Madrid /etc/localtime

#Enabled in Docker
COPY project/ /var/www/html

WORKDIR /var/www/html

EXPOSE 9000

CMD ["php-fpm"]
