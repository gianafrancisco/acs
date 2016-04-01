FROM ubuntu:latest

WORKDIR /

COPY opt/genieacs-gui-master.tar /opt/
COPY config/*.yml /opt/genieacs-gui-master/config/
COPY config/*.erb /opt/genieacs-gui-master/config/
COPY script/init.sh /init.sh

RUN apt-get update && \
	apt-get -y install curl bundler libsqlite3-dev && \
	apt-get clean && \
	cd /opt/ && \
	tar -xvf genieacs-gui-master.tar && \
	cd genieacs-gui-master && \
	bundle

COPY config/environments/* /opt/genieacs-gui-master/config/environments/

EXPOSE 3000

CMD ["sh", "init.sh"]
