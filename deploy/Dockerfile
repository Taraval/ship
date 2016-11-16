# How to build: docker build -t <docker_image_name_here> <docker_file_or_folder>
# Example:      docker build -t deploy4 deploy

# How to run:   docker run --name <name_here> -p <host_port>:<container_port> -d -t <docker_image_name_here>
# Example:      docker run --name delete_me -p 81:80 -d -t deploy3

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
	npm install -g express nodemon && \
    echo "daemon off;" >> /etc/nginx/nginx.conf &&\
	echo "echo starting_service; service isc-dhcp-server start; service nginx start; service tftpd-hpa start; while true; do sleep 2; done" > /start.sh && \
	chmod 755 /start.sh &&\
	echo "Done" 

#EXPOSE 3000

CMD /start.sh
