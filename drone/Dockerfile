# At time of writing, Alpine latest is 3.10
FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
RUN apk update && apk upgrade
# Drone-CI may move to the main repos with future versions of Alpine
RUN apk add --no-cache  drone \
	--repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing
EXPOSE 80
EXPOSE 443
