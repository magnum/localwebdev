FROM php:8.2-apache
RUN apt-get update && \
  apt-get install -y \
  zlib1g-dev \
  less \
  imagemagick \
  libzip-dev \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libpng-dev \
  libwebp-dev \
  nano

RUN docker-php-ext-install mysqli pdo pdo_mysql zip

RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp \
  && docker-php-ext-install gd

# wp-cli
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN chmod +x wp-cli.phar
RUN mv wp-cli.phar /usr/local/bin/wp
RUN alias wp='wp --allow-root'

# ssl
COPY localhost.crt /etc/apache2/ssl/localhost.crt
COPY localhost.key /etc/apache2/ssl/localhost.key
COPY localhost.conf /etc/apache2/sites-enabled/localhost.conf

RUN a2enmod rewrite
RUN a2enmod ssl
RUN chown www-data:www-data /var/www/html/
RUN service apache2 restart
