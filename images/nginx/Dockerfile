FROM nginx:1.18-alpine

ARG USER_ID
RUN addgroup -g $USER_ID app \
    && adduser -G app -u $USER_ID -h /var/www -s /bin/bash -S app
RUN touch /var/run/nginx.pid
RUN mkdir /sock

RUN apk add --no-cache \
    curl \
    nss-tools \
    openssl

RUN mkdir /etc/nginx/certs \
    && echo -e "\n\n\n\n\n\n\n" | openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/certs/nginx.key -out /etc/nginx/certs/nginx.crt

RUN ( \
        cd /usr/local/bin/ \
        && curl -L https://github.com/FiloSottile/mkcert/releases/download/v1.4.1/mkcert-v1.4.1-linux-amd64 -o mkcert \
        && chmod +x mkcert \
    )

RUN chown -R app:app /etc/nginx/certs \
    && chmod -R 755 /etc/nginx/certs

COPY ./conf/nginx.conf /etc/nginx/
COPY ./conf/magento.conf /etc/nginx/
COPY ./conf/default.conf /etc/nginx/conf.d/

RUN mkdir -p /var/www/html \
    && chown -R app:app /etc/nginx /var/www /var/cache/nginx /var/run/nginx.pid /sock

EXPOSE 8443

USER app:app

VOLUME /var/www

WORKDIR /var/www/html