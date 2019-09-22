FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
ENV REFRESHED_AT "2019-09-08"

RUN apk update && apk upgrade 
RUN apk add --no-cache git
RUN wget -O /usr/local/bin/gitea https://dl.gitea.io/gitea/master/gitea-master-linux-arm-6 && \
	chmod +x /usr/local/bin/gitea
RUN addgroup -S git
RUN adduser \
	-S \
	-s /bin/sh \
	-g 'Git Version Control' \
	-G git \
	-D \
	-h /home/git \
	git
RUN mkdir -p /var/lib/gitea/custom/conf && \
	mkdir -p /var/lib/gitea/data && \
	mkdir -p /var/lib/gitea/log && \
	chown -R git:git /var/lib/gitea/ && \
	chmod -R 750 /var/lib/gitea/ && \
	mkdir /etc/gitea && \
	chown root:git /etc/gitea && \
	chmod 770 /etc/gitea 
ENV GITEA_WORK_DIR=/var/lib/gitea/
CMD ["/usr/local/bin/gitea", "web"]
