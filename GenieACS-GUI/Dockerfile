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
	bundle && \
	apt-get -y remove binutils build-essential cpp cpp-4.8 curl dpkg-dev fakeroot g++ g++-4.8 gcc gcc-4.8 krb5-locales libc-dev-bin libc6-dev libgcc-4.8-dev libsqlite3-dev libstdc++-4.8-dev linux-libc-dev make manpages manpages-dev patch ruby-dev ruby1.9.1-dev

COPY config/environments/* /opt/genieacs-gui-master/config/environments/

EXPOSE 3000

CMD ["sh", "init.sh"]
