ARG ALPINE_VERSION=3.19
ARG NODE_VERSION=lts
FROM node:${NODE_VERSION}-alpine${ALPINE_VERSION}

ARG PNPM_VERSION=latest-9
ARG ESSENTIAL_PACKAGES=openssh rsync tree

ENV TZ=Asia/Shanghai
# ENV LANG=en_US.UTF-8

RUN env && apk add --no-cache ${ESSENTIAL_PACKAGES} \
    && rm -rf /var/cache/apk/*
    # && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    # && apk add --no-cache tzdata \
    # && echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    # && locale-gen

# 安装 pnpm
# ref: https://pnpm.io/continuous-integration#gitlab-ci
RUN corepack enable && corepack prepare pnpm@${PNPM_VERSION} --activate

