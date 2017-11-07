FROM php:7.0.22-fpm

#Install
RUN apt-get update \
  && apt-get install -y \
    cron \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    libxslt1-dev

RUN docker-php-ext-configure \
  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install \
  bcmath \
  gd \
  intl \
  mbstring \
  mcrypt \
  pdo_mysql \
  soap \
  xsl \
  zip

RUN curl -sS https://getcomposer.org/installer | \
  php -- --install-dir=/usr/local/bin --filename=composer

# Configure
COPY ./www.conf /usr/local/etc/php-fpm.d/
COPY ./php.ini /usr/local/etc/php/
# COPY ./php-fpm.conf /usr/local/etc/
# COPY ./* /usr/local/bin/

# Make sure the volume mount point is empty
# RUN rm -rf /var/www/html/*

# Install magerun
# RUN curl -o magerun https://raw.githubusercontent.com/netz98/n98-magerun/master/n98-magerun.phar && \
#     chmod +x ./magerun && \
#     cp ./magerun /usr/local/bin/ && \
#     rm ./magerun && \
#     apt-get update && \
#     apt-get install -qy mysql-client
