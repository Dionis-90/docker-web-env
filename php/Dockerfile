FROM php:7.2-fpm

RUN apt-get update && apt-get install -y \
curl \
wget \
git \
libfreetype6-dev \
libjpeg62-turbo-dev \
libxslt-dev \
libicu-dev \
unzip \
#libmcrypt-dev \
#libpng12-dev \
libxml2-dev
#python3-pycurl

#RUN docker-php-ext-install -j$(nproc) mysqli gd opcache pdo_mysql zip \
#&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
#&& docker-php-ext-install -j$(nproc) gd
#&& docker-php-ext-enable gd pdo_mysql zip curl opcache mbstring

#RUN docker-php-ext-configure intl
#RUN docker-php-ext-install intl
#RUN docker-php-ext-install xsl
RUN docker-php-ext-install soap mysqli gd opcache pdo_mysql zip
#RUN docker-php-ext-install mcrypt

RUN cd /tmp \
	&& curl -o ioncube.tar.gz http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
    && tar -xvzf ioncube.tar.gz \
    && mv ioncube/ioncube_loader_lin_7.2.so /usr/local/lib/php/extensions/* \
    && rm -Rf ioncube.tar.gz ioncube \
    && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20170718/ioncube_loader_lin_7.2.so" > /usr/local/etc/php/conf.d/00_docker-php-ext-ioncube_loader_lin_7.2.ini

#RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

WORKDIR /var/www/seotaster

CMD ["php-fpm"]
