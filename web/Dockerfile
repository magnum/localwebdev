FROM php:7.2-apache
RUN apt-get update && \
  apt-get install -y \
  zlib1g-dev
COPY localhost.crt /etc/apache2/ssl/localhost.crt
COPY localhost.key /etc/apache2/ssl/localhost.key
COPY localhost.conf /etc/apache2/sites-enabled/localhost.conf
RUN docker-php-ext-install mysqli pdo pdo_mysql zip mbstring
RUN a2enmod rewrite
RUN a2enmod ssl
RUN chown www-data:www-data /var/www/html/
RUN service apache2 restart