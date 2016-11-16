FROM ubuntu
MAINTAINER taraval

RUN apt-get update

RUN apt-get install isc-dhcp-server tftpd-hpa nginx -y

RUN echo "daemon off;" >> /etc/nginx/nginx.conf

EXPOSE 8181

CMD service nginx start