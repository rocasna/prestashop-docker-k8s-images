FROM nginx:1.23.1

RUN apt-get update  && \
    apt-get install wget nano curl -y

COPY default.conf /etc/nginx/conf.d/

RUN mkdir -p /var/www/html

COPY check.html /var/www/html

WORKDIR /var/www/html

CMD ["nginx", "-g", "daemon off;"]