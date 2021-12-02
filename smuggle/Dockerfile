FROM alpine

# copy your data to "files" folder
COPY ./files /data/files
WORKDIR "/data"
RUN apk update ; \
    apk --no-cache add curl \
                       tar \
                       gzip \
                       openssl ; \ 

    

# download data to "/data/files"
    # mkdir -p /data/files ; \
    # curl -L https://github.com/roccqqck/dockerfiles/archive/refs/heads/main.zip -o /data/files/main.zip ; \
    tar -czvf /data/files.tar.gz  /data/files ; \  
    chmod -R 777 /data ; \

    rm -rf /data/files ; \

    apk del curl tar gzip openssl    ;\
    rm -rf /var/cache/apk/*