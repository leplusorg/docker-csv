FROM alpine:3.18.2

# hadolint ignore=DL3018
RUN apk --update --no-cache add coreutils gawk grep g++ icu-dev python3 python3-dev py3-pip sed \
    && rm -rf /var/cache/apk/*

# hadolint ignore=DL3013
RUN pip3 install --no-cache-dir --upgrade csvkit
