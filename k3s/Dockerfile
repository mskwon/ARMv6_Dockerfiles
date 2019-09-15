FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
ENV REFRESHED_AT "2019-09-14"

RUN apk update && apk upgrade
# k3s and cni-plugins may move to the main repos with future versions of Alpine
RUN apk add --no-cache  k3s cni-plugins \
	--repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing
ENV PATH /usr/share/cni-plugins/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

