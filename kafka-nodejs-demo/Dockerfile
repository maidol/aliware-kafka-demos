FROM registry.cn-beijing.aliyuncs.com/jiaofuyun/alinode:3.8.4-alpine
LABEL Name=kafka-nodejs-demo Version=1.0.0

RUN apk --no-cache add \
      # ca-certificates \
      lz4-dev \
      musl-dev \
      cyrus-sasl-dev \
      openssl-dev

RUN mkdir -p /var/app
WORKDIR /var/app

COPY ./package.json /var/app

RUN apk add --no-cache --virtual .build-deps \
      g++ \
      make \
      python \
      gcc \
      zlib-dev \
      libc-dev \
      bsd-compat-headers \
      py-setuptools \
      bash \
      && npm install --production --registry=https://registry.npm.taobao.org \
      && apk del .build-deps

COPY . /var/app/

CMD node consumer.js
