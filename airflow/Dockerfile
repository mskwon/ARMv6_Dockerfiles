FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
ENV REFRESHED_AT "2019-09-15"

RUN apk update && apk upgrade
RUN apk add --no-cache 	py3-numpy \
			py3-setproctitle \
			py3-lxml \
			py3-psutil \
			py3-gunicorn \
			py3-jinja2 \
			py3-babel
# py3-pandas may move to the main repo with later version of Alpine
RUN apk add --no-cache  py3-pandas \
	--repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing

# apache-airflow dependencies
RUN apk add --no-cache gcc musl-dev

RUN pip3 install --no-cache-dir apache-airflow
EXPOSE 8080
