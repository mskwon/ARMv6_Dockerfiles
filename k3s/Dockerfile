FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
ENV REFRESHED_AT "2019-09-14"

RUN apk update && apk upgrade
# k3s may move to the main repos with future versions of Alpine
RUN apk add --no-cache  k3s \
	--repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing
