FROM bitnami/nginx:1.20

USER root
ENV TZ=Asia/Taipei
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone ; \
    mkdir -p  /opt/bitnami/nginx/html/api/patha/ ; \

    cp /opt/bitnami/nginx/html/index.html  /opt/bitnami/nginx/html/api/patha/ ; \

    echo '<html><body><h1>Hello World patha</h1></body></html>' >> /opt/bitnami/nginx/html/api/patha/index.html


USER 1001