FROM php:7.2-fpm

LABEL version="1.0"
LABEL Description="PHP FPM pp_cus_7.2.18"
LABEL maintainer="bruce<heyuan110@gmail.com>" 
LABEL dockerhub="https://hub.docker.com/u/heyuan110"
LABEL github="https://github.com/heyuan110/docker-app"

#redis version
ENV  REDIS_VERSION=4.0.1

#install php extensions, -j$(nproc)表示调用CPU可用的核进行并行编译，可以加快便已速度。
RUN apt-get update \
    && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libpng-dev \
    #install Composer globally
    && curl -s -o /usr/local/bin/composer https://getcomposer.org/composer.phar \
    && chmod 0755 /usr/local/bin/composer \
    # gd扩展
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    # gettext bcmath pdo_mysql 扩展
    && docker-php-ext-install -j$(nproc) bcmath gettext pdo_mysql \
    # redis 扩展
    && pecl install redis-${REDIS_VERSION} \
    && docker-php-ext-enable redis \
    # 增加 mcrypt 扩展 
    && apt-get install -y --no-install-recommends libmcrypt-dev \
    && pecl install mcrypt-1.0.1 \
    && docker-php-ext-enable mcrypt \
    # 增加 zip 扩展
    && apt-get install -y --no-install-recommends libzip-dev\
    && docker-php-ext-install -j$(nproc) zip \
    # 增加 zip 扩展
    && pecl install mongo \
    && echo "extension=mongo.so" > /usr/local/etc/php/conf.d/ext-mongo.ini \
    # 清理文件
    && rm -r /var/lib/apt/lists/* \