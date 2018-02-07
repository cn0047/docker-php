FROM cn007b/php:7.1-composer

# protobuf 2
RUN curl -OL https://github.com/google/protobuf/releases/download/v2.6.1/protobuf-2.6.1.tar.gz \
    && tar xzf protobuf-2.6.1.tar.gz \
    && cd protobuf-2.6.1 \
    && apt-get update && apt-get install -y build-essential \
    && ./configure && make && make install \
    && ldconfig \
    && cd - && rm protobuf-2.6.1.tar.gz && rm -rf protobuf-2.6.1

# php-protobuf
RUN pecl channel-update pecl.php.net \
    && pear install Console_CommandLine \
    && pear channel-discover pear.pollinimini.net \
    && pear install drslump/Protobuf-beta
