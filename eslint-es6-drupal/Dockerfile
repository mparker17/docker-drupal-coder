FROM node:10.15
WORKDIR /opt/drupal
RUN curl -o 'package.json' -L 'https://git.drupalcode.org/project/drupal/raw/3c5675d1b20146ee66c245f57d850bcfffe87a0e/core/package.json' && \
  npm install && \
  curl -o '.eslintrc.json' -L 'https://git.drupalcode.org/project/drupal/raw/3c5675d1b20146ee66c245f57d850bcfffe87a0e/core/.eslintrc.json'
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/drupal/node_modules/.bin/eslint", "-c", "/opt/drupal/.eslintrc.json"]
