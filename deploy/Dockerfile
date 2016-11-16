FROM ubuntu
MAINTAINER taraval

ENV NODE_VERSION 6.9.1
ENV PROJECT_NAME deploy

RUN apt-get update && \
    apt-get install isc-dhcp-server tftpd-hpa nginx xz-utils curl -y && \
	apt-get clean && \
    apt-get -y autoremove && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir -p /repox/$PROJECT_NAME && \
	cd /repox/$PROJECT_NAME && curl -SLO "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.xz" && \
	tar -xJf "node-v$NODE_VERSION-linux-x64.tar.xz" -C /usr/local/ --strip-components=1 && \
	rm "node-v$NODE_VERSION-linux-x64.tar.xz" && \
    echo "daemon off;" >> /etc/nginx/nginx.conf &&\
	echo "Done" 

#EXPOSE 8181

CMD service nginx start