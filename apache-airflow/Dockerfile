# At time of writing, alpine latest is 3.10
FROM arm32v6/alpine
LABEL maintainer="michael.s.kwon@gmail.com"
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
RUN pip3 install --no-cache-dir apache-airflow
EXPOSE 8080
