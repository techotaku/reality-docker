FROM bitnami/nginx

LABEL maintainer "Ian Li <OpenSource@ianli.xyz>"

USER root

RUN apt-get update && apt-get install -y curl nano ca-certificates tzdata && \
    apt-get clean && rm -rf /var/lib/apt/lists /var/cache/apt/archives && \
    curl -O https://raw.githubusercontent.com/tests-always-included/mo/master/mo && \
    mv mo /usr/local/bin && \
    chmod +x /usr/local/bin/mo && \
    curl -sSL https://github.com/techotaku/reality-docker/raw/main/forwarder/nginx.conf.template -o /opt/bitnami/nginx/conf/nginx.conf.template && \
    curl -sSL https://github.com/techotaku/reality-docker/raw/main/forwarder/configure-and-run.sh -o /app/configure-and-run.sh && \
    chmod +x /app/configure-and-run.sh

ENV TZ=Asia/Shanghai

USER 1001

ENTRYPOINT []

CMD [ "/app/configure-and-run.sh" ]
