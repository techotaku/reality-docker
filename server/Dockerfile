FROM alpine

LABEL maintainer "Ian Li <OpenSource@ianli.xyz>"

RUN apk add --no-cache bash curl nano ca-certificates tzdata && \
    curl -sSL https://github.com/XTLS/Xray-core/releases/download/v1.8.16/Xray-linux-64.zip -o /tmp/xray.zip && \
    mkdir -p /tmp/xray && \
    unzip /tmp/xray.zip -d /tmp/xray/ && \
    mv /tmp/xray/xray /usr/local/bin/xray && \
    mv /tmp/xray/geoip.dat /usr/local/bin/geoip.dat && \
    mv /tmp/xray/geosite.dat /usr/local/bin/geosite.dat && \
    chmod +x /usr/local/bin/xray && \
    rm -rf /tmp/xray && \
    curl -O https://raw.githubusercontent.com/tests-always-included/mo/master/mo && \
    mv mo /usr/local/bin && \
    chmod +x /usr/local/bin/mo && \
    curl -sSL https://github.com/hjson/hjson-go/releases/download/v4.4.0/hjson_v4.4.0_linux_amd64.tar.gz | tar -xz -C /usr/local/bin && \
    mkdir -p /etc/xray/ && \
    curl -sSL https://github.com/techotaku/reality-docker/raw/main/server/config.json.template -o /etc/xray/config.json.template && \
    curl -sSL https://github.com/techotaku/reality-docker/raw/main/server/configure-and-run.sh -o /root/configure-and-run.sh && \
    chmod +x /root/configure-and-run.sh

ENV TZ=Asia/Shanghai

CMD [ "/root/configure-and-run.sh" ]
