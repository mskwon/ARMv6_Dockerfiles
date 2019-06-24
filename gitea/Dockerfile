# At time of writing, alpine latest is 3.10
FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
RUN apk update && apk upgrade
RUN apk add --no-cache  git
# Cross compiled using:
# 	go get -d -u code.gitea.io/gitea
#	cd "$GOPATH/src/code.gitea.io/gitea"
#	make generate
#	GOOS=linux GOARCH=arm GOARM=6 TAGS="bindata" make build
COPY ./gitea /usr/bin
EXPOSE 3000
