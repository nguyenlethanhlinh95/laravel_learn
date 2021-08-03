FROM php:7.4.4-fpm

# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim

RUN apt-get update \
    && apt-get install -y libpq-dev libpng-dev \
    && docker-php-ext-install pdo_mysql pdo_pgsql

RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev

RUN apt-get update \
	&& apt-get install -y \
		libmagickwand-dev --no-install-recommends \
		ghostscript --no-install-recommends \
	&& pecl install \
		imagick \
	&& docker-php-ext-enable \
		imagick \
	&& apt-get purge -y \
		libmagickwand-dev

RUN docker-php-ext-install gd
RUN docker-php-ext-install fileinfo
RUN docker-php-ext-install exif

WORKDIR /var/www/html

