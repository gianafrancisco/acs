FROM alpine:3.3

RUN apk add --update musl-dev g++ gcc make python nodejs git && \
	rm -rf /var/cache/apk/* && \
	mkdir /opt/ && \
	cd /opt/ && \
	git clone https://github.com/zaidka/genieacs.git --branch v1.0 && \
	cd genieacs && \
	npm install && npm run configure && npm run compile && \
	apk del musl-dev g++ gcc make python git 

COPY opt/config.json /opt/genieacs/config/

EXPOSE 7547  
CMD ["/opt/genieacs/bin/genieacs-cwmp"]
#EXPOSE 7557
#CMD ["/opt/genieacs/bin/genieacs-nbi"]
#EXPOSE 7567
#CMD ["/opt/genieacs/bin/genieacs-fs"]