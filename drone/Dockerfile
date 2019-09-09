FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
ENV REFRESHED_AT "2019-09-08"

RUN apk update && apk upgrade
# Drone-CI may move to the main repos with future versions of Alpine
RUN apk add --no-cache  drone \
	--repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing
EXPOSE 8080 443
