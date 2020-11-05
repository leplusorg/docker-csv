FROM alpine:latest

RUN apk --update --no-cache add coreutils gawk grep python3 py3-pip sed \
    && rm -rf /var/cache/apk/*

RUN pip3 install --upgrade csvkit
