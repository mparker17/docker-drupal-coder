FROM node:10.15
WORKDIR /opt/drupal
RUN curl -o 'package.json' -L 'https://git.drupalcode.org/project/drupal/-/raw/8a9f88169a7c3b6a00636d5e0c4c9f8988d92499/core/package.json' && \
  npm install && \
  curl -o '.stylelintrc.json' -L 'https://git.drupalcode.org/project/drupal/-/raw/8a9f88169a7c3b6a00636d5e0c4c9f8988d92499/core/.stylelintrc.json'
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/drupal/node_modules/.bin/stylelint", "--config", "/opt/drupal/.stylelintrc.json"]
