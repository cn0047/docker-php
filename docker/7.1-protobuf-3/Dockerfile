FROM cn007b/php:7.1

MAINTAINER Vladimir Kovpak <cn007b@gmail.com>

# protobuf 3
RUN pecl install protobuf-3.5.1 \
    && echo 'extension=protobuf.so' >> /etc/php/7.1/mods-available/protobuf.ini

# php-protobuf
RUN pecl channel-update pecl.php.net \
    && pear install Console_CommandLine
