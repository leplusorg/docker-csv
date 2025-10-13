FROM alpine:3.22.2@sha256:4b7ce07002c69e8f3d704a9c5d6fd3053be500b7f1c69fc0d80990c2ad8dd412

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    coreutils=9.7-r1 \
    csvq=1.18.1-r20 \
    curl=8.14.1-r2 \
    dasel=2.8.1-r7 \
    gawk=5.3.2-r2 \
    git=2.49.1-r0 \
    grep=3.12-r0 \
    miller=6.13.0-r7 \
    pandoc-cli=3.6.4-r0 \
    pipx=1.7.1-r0 \
    py3-pip=25.1.1-r0 \
    python3=3.12.12-r0 \
    sed=4.9-r2 \
    yq-go=4.47.2-r0 \
    && apk cache --no-cache clean \
    && rm -rf /var/cache/apk/*

RUN pipx ensurepath --global \
    && pipx install --global \
    csvkit==2.1.0 \
    remarshal==1.2.0

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

USER "${USER_NAME}"

ENV HOME="${USER_HOME}"

WORKDIR "${HOME}"
