# At time of writing, alpine latest is 3.10
FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
RUN apk update && apk upgrade
RUN apk add --no-cache  gitea
EXPOSE 3000
