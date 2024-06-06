ARG ALPINE_VERSION=3.19
FROM alpine:${ALPINE_VERSION}

# issue: https://stackoverflow.com/a/56748289/2117999
ARG ESSENTIAL_PACKAGES=openssh rsync tree

ENV TZ=Asia/Shanghai
# ENV LANG=en_US.UTF-8

RUN env && apk add --no-cache ${ESSENTIAL_PACKAGES} \
    && rm -rf /var/cache/apk/*
    # && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    # && apk add --no-cache tzdata \
    # && echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    # && locale-gen
