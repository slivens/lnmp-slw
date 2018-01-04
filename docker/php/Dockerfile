FROM php:7.1.0-fpm

RUN printf "\n" | pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis

RUN apt-get update && \
    apt-get install -y \
    zlib1g-dev

RUN docker-php-ext-install zip

RUN curl -sS https://getcomposer.org/installer | php && \
     mv composer.phar /usr/local/bin/composer && \
     chmod -R +x /usr/local/bin/composer

RUN echo "" >> ~/.bashrc && \
	echo 'export PATH="~/.composer/vendor/bin:$PATH"' >> ~/.bashrc \
	&& composer global require "laravel/installer" 

WORKDIR /var/www

RUN docker-php-ext-install pdo_mysql
