FROM alpine:latest

RUN apk --update --no-cache add coreutils csvtool gawk grep python3 sed \
    && rm -rf /var/cache/apk/*

RUN pip install --upgrade csvkit
