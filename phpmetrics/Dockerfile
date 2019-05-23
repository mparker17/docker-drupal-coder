FROM composer:1.8.5
WORKDIR /opt/phpmetrics
RUN composer require 'phpmetrics/phpmetrics:2.4.1'
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/phpmetrics/vendor/bin/phpmetrics"]
