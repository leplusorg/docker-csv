FROM alpine:latest

RUN apk --update --no-cache add coreutils gawk grep python3 sed \
    && apk --update --no-cache add -X http://dl-cdn.alpinelinux.org/alpine/edge/testing csvtool \
    && rm -rf /var/cache/apk/*

RUN pip3 install --upgrade csvkit
