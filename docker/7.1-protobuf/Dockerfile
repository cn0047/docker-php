FROM cn007b/php:7.1-composer

# protobuf 2
RUN curl -OL https://github.com/google/protobuf/releases/download/v2.6.1/protobuf-2.6.1.tar.gz \
    && tar xzf protobuf-2.6.1.tar.gz \
    && cd protobuf-2.6.1 \
    && apt-get update && apt-get install -y build-essential \
    && ./configure && make && make install \
    && ldconfig \
    && cd - && rm protobuf-2.6.1.tar.gz && rm -rf protobuf-2.6.1

# protobuf 3
#RUN curl -OL https://github.com/google/protobuf/releases/download/v3.5.1/protoc-3.5.1-linux-x86_64.zip \
#    && unzip protoc-3.5.1-linux-x86_64.zip -d protoc3 \
#    && mv protoc3/bin/* /usr/local/bin/ \
#    && mv protoc3/include/* /usr/local/include/ \
#    && chown $(whoami) /usr/local/bin/protoc \
#    && chown -R $(whoami) /usr/local/include/google \
#    && pecl install protobuf-3.5.1 \
#    && echo 'extension=protobuf.so' >> /etc/php/7.1/mods-available/protobuf.ini \
#    && rm protoc-3.5.1-linux-x86_64.zip

# php-protobuf
RUN pecl channel-update pecl.php.net \
    && pear install Console_CommandLine \
    && pear channel-discover pear.pollinimini.net \
    && pear install drslump/Protobuf-beta
