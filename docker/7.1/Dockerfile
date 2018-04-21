FROM cn007b/ubuntu:17.10-protobuf-3

MAINTAINER Vladimir Kovpak <cn007b@gmail.com>

RUN apt-get update

# php
RUN apt-get install -y \
    php7.1 php7.1-cli php7.1-opcache php7.1-common php7.1-phpdbg php7.1-dev \
    php7.1-mcrypt php7.1-mbstring php7.1-bcmath php7.1-gd php7.1-zip php7.1-curl php7.1-imagick \
    php7.1-imap php7.1-ldap \
    php7.1-dom php7.1-xml php7.1-json \
    php7.1-mysql php7.1-pdo php-mongodb php7.1-sqlite php7.1-sqlite3 php7.1-pgsql \
    php7.1-redis \
    php7.1-memcache \
    php-zmq \
    php-pear php-soap php-ssh2

# xdebug
RUN apt-get install -y php-xdebug \
    && echo 'xdebug.remote_enable=1'            >> /etc/php/7.1/mods-available/xdebug.ini \
    && echo 'xdebug.remote_autostart=1'         >> /etc/php/7.1/mods-available/xdebug.ini \
    # IMPORTANT: On OSX this config value must be 0.
    && echo 'xdebug.remote_connect_back=0'      >> /etc/php/7.1/mods-available/xdebug.ini \
    # IMPORTANT: On OSX run next command:
    # sudo ifconfig lo0 alias 10.254.254.254
    && echo 'xdebug.remote_host=10.254.254.254' >> /etc/php/7.1/mods-available/xdebug.ini \
    && echo 'xdebug.remote_port=9002'           >> /etc/php/7.1/mods-available/xdebug.ini \
    && echo 'xdebug.idekey=PHPSTORM'            >> /etc/php/7.1/mods-available/xdebug.ini

# php conf
RUN    echo 'display_errors=On'           >> /etc/php/7.1/cli/php.ini \
    && echo 'display_startup_errors=On'   >> /etc/php/7.1/cli/php.ini \
    && echo 'track_errors=On'             >> /etc/php/7.1/cli/php.ini \
    && echo 'log_errors=On'               >> /etc/php/7.1/cli/php.ini \
    && echo 'error_log=/dev/stdout'       >> /etc/php/7.1/cli/php.ini

# for Yii 1 template engine
RUN echo 'short_open_tag=On' >> /etc/php/7.1/cli/php.ini

# for big files upload.
RUN echo 'upload_max_filesize=50M' >> /etc/php/7.1/cli/php.ini

# composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# phpcs
RUN curl -OL https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar \
    && chmod +x phpcs.phar \
    && cp phpcs.phar /usr/local/bin/phpcs \
    && cp phpcs.phar /usr/bin/phpcs \
    && rm phpcs.phar
