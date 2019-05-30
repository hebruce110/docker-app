FROM php:5.6-fpm

LABEL version="1.0"
LABEL Description="PHP FPM pp_cus_5.6"
LABEL maintainer="bruce<heyuan110@gmail.com>" 
LABEL dockerhub="https://hub.docker.com/u/heyuan110"
LABEL github="https://github.com/heyuan110/docker-app"

#redis version
ENV  REDIS_VERSION=4.0.1

#install php extensions, -j$(nproc)表示调用CPU可用的核进行并行编译，可以加快便已速度。
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libpng-dev \
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
    # 1.0.8 增加 zip 扩展
    && apt-get install -y --no-install-recommends libzip-dev\
    && docker-php-ext-install -j$(nproc) zip \
    # 清理文件
    && rm -r /var/lib/apt/lists/* \