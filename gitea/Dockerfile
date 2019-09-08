FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
ENV REFRESHED_AT "2019-09-08"

RUN apk update && apk upgrade
RUN apk add --no-cache gitea
EXPOSE 3000 22

WORKDIR /tmp
RUN git clone --depth=1 https://github.com/go-gitea/gitea.git && \
	mkdir /usr/bin/custom && \
	mv /tmp/gitea/options /usr/bin/custom/conf && \
	rm -rf /tmp/gitea
WORKDIR /usr/bin/custom

CMD ["gitea", "web"]


