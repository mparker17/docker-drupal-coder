FROM node:12.13
COPY package.json /opt/jsonlint/package.json
WORKDIR /opt/jsonlint
RUN npm install
WORKDIR /app
VOLUME /app
ENTRYPOINT ["/opt/jsonlint/node_modules/.bin/jsonlint", "-q"]
