FROM alpine:3.15.0

RUN apk --update --no-cache add coreutils gawk grep g++ icu-dev python3 python3-dev py3-pip sed \
    && rm -rf /var/cache/apk/*

RUN pip3 install --upgrade csvkit
