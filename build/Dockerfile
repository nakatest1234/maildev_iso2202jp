FROM djfarrelly/maildev:1.1.0

LABEL maintainer="nakatest1234, twitter:@ambient2step" \
      Description="maildev for ISO-2202-JP"

ENV NODE_ENV production
ENV APP_TZ   Asia/Tokyo
ENV DEPS     gcc make g++ python

WORKDIR /usr/src/app

RUN apk update -q --no-cache ca-certificates \
    && apk add -q --no-cache tzdata ${DEPS} \
    && cp -f /usr/share/zoneinfo/${APP_TZ} /etc/localtime \
    && npm config set unsafe-perm true \
    && npm --silent install node-gyp \
    && npm --silent install iconv \
    && npm --silent prune \
    && npm --silent cache verify \
    && apk del -q tzdata ${DEPS} \
    && rm -Rf ~/.npm/_cacache ~/.npm/_logs \
    && :
