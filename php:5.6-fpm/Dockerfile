FROM php:5.6-fpm

RUN apt-get -y update && apt-get -y upgrade && apt-get install -y \ 
		libmcrypt-dev \
		libjpeg-dev \
		libpng12-dev \
		libpq-dev \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
	&& docker-php-ext-install \
		gd \
		json \
		mbstring \
		mcrypt \
		mysql \
		mysqli \
		pdo \
		pdo_mysql \
		pdo_pgsql \
		zip \
		opcache 

# set recommended PHP.ini settings
# see https://secure.php.net/manual/en/opcache.installation.php
RUN { \
		echo 'opcache.memory_consumption=128'; \
		echo 'opcache.interned_strings_buffer=8'; \
		echo 'opcache.max_accelerated_files=4000'; \
		echo 'opcache.revalidate_freq=2'; \
		echo 'opcache.fast_shutdown=1'; \
		echo 'opcache.enable_cli=1'; \
	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
