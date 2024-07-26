ARG ALPINE_VERSION=3.19
FROM alpine:${ALPINE_VERSION}

# issue: https://stackoverflow.com/a/56748289/2117999
ARG ESSENTIAL_PACKAGES=jq tree ca-certificates curl bash
# https://github.com/a8m/envsubst
# ttps://github.com/a8m/envsubst/releases
ARG ENVSUBST_VERSION=v1.4.2
ARG KUBECTL_VERSION=v1.30.3

# Install required system packages and dependencies
# RUN install_packages ca-certificates curl gettext git jq procps
# ref: https://github.com/bitnami/containers/blob/main/bitnami/kubectl/1.29/debian-12/Dockerfile

ENV TZ=Asia/Shanghai
# ENV LANG=en_US.UTF-8

RUN env && apk add --no-cache ${ESSENTIAL_PACKAGES} \
    && rm -rf /var/cache/apk/*
    # && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    # && apk add --no-cache tzdata \
    # && echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    # && locale-gen

# install envsubst
RUN curl -L https://github.com/a8m/envsubst/releases/download/${ENVSUBST_VERSION}/envsubst-`uname -s`-`uname -m` -o /usr/local/bin/envsubst \
    && chmod +x /usr/local/bin/envsubst

# install kustomize
# https://github.com/kubernetes-sigs/kustomize/releases/download/kustomize%2Fv5.4.3/kustomize_v5.4.3_linux_amd64.tar.gz
RUN cd /usr/local/bin/ && curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash

# install kubectl
# https://dl.k8s.io/v1.30.3/bin/linux/amd64/kubectl
#  docker run --rm -it --entrypoint sh ghcr.nju.edu.cn/junxy/alpine:kubectl-kustomize-envsubst
#  which kubectl | xargs cat
# RUN curl -L "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/linux/amd64/kubectl" -o /usr/local/bin/kubectl \
RUN curl -L https://dl.k8s.io/${KUBECTL_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl \
    && chmod +x /usr/local/bin/kubectl

# mark
RUN touch $(date '+%Y%m%d%H%M%S')

# USER 1001
ENTRYPOINT [ "kubectl" ]
CMD [ "--help" ]
