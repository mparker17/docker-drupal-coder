FROM composer:1.8.5
WORKDIR /opt/dephpend
RUN composer require 'dephpend/dephpend:0.6.0'
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/dephpend/vendor/bin/dephpend"]
