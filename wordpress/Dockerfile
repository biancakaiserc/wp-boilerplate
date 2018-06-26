FROM php:7.1-apache

#------------------------
# Packages
#------------------------
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libmcrypt-dev \
    unzip \
    git \
    nano \
    mysql-client \
    netcat

#------------------------
# PHP Extensions
#------------------------
RUN docker-php-ext-install -j$(nproc)\
    pdo pdo_mysql \
    bcmath gettext \
    calendar zip \
    mcrypt mysqli \
    opcache

RUN docker-php-ext-configure gd \
    --with-gd \
    --with-png-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

#------------------------
# Xdebug Extensions
#------------------------
RUN yes | pecl install xdebug \
    && docker-php-ext-enable xdebug

#------------------------
# Composer
#------------------------
RUN curl -s http://getcomposer.org/installer | php \
    && echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc \
    && mv composer.phar /usr/local/bin/composer

#------------------------
# Apache configuration
#------------------------
RUN a2enmod rewrite
RUN service apache2 restart

#------------------------
# Bash config
#------------------------
RUN git clone --depth=1 https://github.com/Bash-it/bash-it.git /.bash_it \
    && /.bash_it/install.sh

RUN rm -rf /tmp/*

# Configure entrypoint
COPY ./docker-entrypoint.sh /
RUN ["chmod", "+x", "/docker-entrypoint.sh"]

WORKDIR /var/www/html

ENTRYPOINT ["/docker-entrypoint.sh"]
