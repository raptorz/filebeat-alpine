FROM alpine:3.8

MAINTAINER raptor<raptor.zh@gmail.com>

WORKDIR /var/temp

ENV FILEBEAT_VERSION=6.4.1

ADD ./filebeat.yml /etc/filebeat/

# Only for China
# RUN ( echo "https://mirrors.ustc.edu.cn/alpine/v3.8/main" > /etc/apk/repositories ) \
#     && ( echo "https://mirrors.ustc.edu.cn/alpine/v3.8/community" >> /etc/apk/repositories ) \
#     && apk update && apk upgrade && apk add --no-cache tzdata \
#     && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
#     && ( echo "Asia/Shanghai" > /etc/timezone )
RUN apk add --no-cache curl libc6-compat && \
    rm -rf /var/cache/apk/* && \
    curl https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-linux-x86_64.tar.gz -o filebeat.tar.gz && \
    tar xzvf filebeat.tar.gz && \
    mv filebeat-${FILEBEAT_VERSION}-linux-x86_64/filebeat /usr/bin && \
    rm filebeat.tar.gz && \
    rm -rf filebeat-${FILEBEAT_VERSION}-linux-x86_64 && \
    chown root.root /etc/filebeat/filebeat.yml && \
    chmod go-w /etc/filebeat/filebeat.yml && \
    ls -ltr

CMD ["/usr/bin/filebeat","-e","-c","/etc/filebeat/filebeat.yml"]
