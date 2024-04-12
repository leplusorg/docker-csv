FROM alpine:3.19.1@sha256:c5b1261d6d3e43071626931fc004f70149baeba2c8ec672bd4f27761f8e1ad6b

# hadolint ignore=DL3018
RUN apk --update --no-cache add coreutils csvq gawk grep g++ icu-dev python3 python3-dev py3-pip sed \
    && rm -rf /var/cache/apk/*

# hadolint ignore=DL3013
RUN pip3 install --no-cache-dir --upgrade --break-system-packages csvkit

ARG USER=default

ENV HOME "/home/${USER}"

RUN adduser -D "${USER}"

USER "${USER}"

WORKDIR "${HOME}"