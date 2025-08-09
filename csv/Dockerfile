FROM alpine:3.22.1@sha256:4bcff63911fcb4448bd4fdacec207030997caf25e9bea4045fa6c8c44de311d1

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

# hadolint ignore=DL3019
RUN apk -U upgrade \
    && apk add \
    coreutils=9.7-r1 \
    csvq=1.18.1-r18 \
    curl=8.14.1-r1 \
    gawk=5.3.2-r2 \
    git=2.49.1-r0 \
    grep=3.12-r0 \
    g++=14.2.0-r6 \
    icu-dev=76.1-r1 \
    py3-pip=25.1.1-r0 \
    python3=3.12.11-r0 \
    sed=4.9-r2 \
    && if apk -u list | grep -q -e . ; then \
      apk -u list ; \
      exit 1 ; \
    fi \
    && apk cache clean \
    && rm -rf /var/cache/apk/*

RUN pip3 install --no-cache-dir --upgrade --break-system-packages \
    csvkit==2.1.0 \
    && msg="$(pip3 list --outdated | grep -i -e '^csvkit ' || true)" \
    && if [ -n "${msg}" ]; then \
       >&2 echo "ERROR: outdated: ${msg}" ; \
       exit 1 ; \
    fi

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

USER "${USER_NAME}"

ENV HOME="${USER_HOME}"

WORKDIR "${HOME}"
