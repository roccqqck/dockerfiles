FROM azul/zulu-openjdk-alpine:11-jre-headless

RUN apk update ; \
    apk --no-cache add curl \
                       bash \
                       openssl \
                       ca-certificates \
                       tzdata \ 
                       ttf-dejavu ;\

    cp /usr/share/zoneinfo/Asia/Taipei /etc/localtime ;\
    echo "Asia/Taipei" > /etc/timezone ;\


    apk del tzdate    ;\
    rm -rf /var/cache/apk/*