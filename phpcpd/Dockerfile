FROM composer:1.8.5
WORKDIR /opt/phpcpd
RUN composer require 'sebastian/phpcpd:4.1.0'
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/phpcpd/vendor/bin/phpcpd"]
