FROM alpine:3.21.3@sha256:a8560b36e8b8210634f77d9f7f9efd7ffa463e380b75e2e74aff4511df3ef88c

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
    coreutils=9.5-r2 \
    csvq=1.18.1-r14 \
    gawk=5.3.1-r0 \
    grep=3.11-r0 \
    g++=14.2.0-r4 \
    icu-dev=74.2-r0 \
    py3-pip=24.3.1-r0 \
    python3=3.12.9-r0 \
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

ENV HOME="${USER_HOME}"

USER "${USER_NAME}"

WORKDIR "${HOME}"
