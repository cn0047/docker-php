FROM cn007b/php:7.1-protobuf-3

MAINTAINER Vladimir Kovpak <cn007b@gmail.com>

# php-fpm
RUN apt-get install -y php7.1 php7.1-fpm

# php-fpm conf
RUN    echo 'display_errors=On'           >> /etc/php/7.1/fpm/php.ini \
    && echo 'display_startup_errors=On'   >> /etc/php/7.1/fpm/php.ini \
    && echo 'track_errors=On'             >> /etc/php/7.1/fpm/php.ini \
    && echo 'log_errors=On'               >> /etc/php/7.1/fpm/php.ini \
    && echo 'error_log=/dev/stdout'.      >> /etc/php/7.1/fpm/php.ini

# php-fpm conf for Yii 1 template engine
RUN echo 'short_open_tag=On' >> /etc/php/7.1/fpm/php.ini

# php-fpm conf for big files upload.
RUN echo 'upload_max_filesize=50M' >> /etc/php/7.1/fpm/php.ini

# nginx
RUN apt-get install -y nginx
COPY nginx.conf /etc/nginx/conf.d/default.conf
