FROM arm32v6/docker

RUN apk update && apk upgrade && apk add --no-cache openjdk8 git openssh-client curl unzip bash ttf-dejavu coreutils tini

ARG user=jenkins
ARG group=jenkins
ARG uid=1000
ARG gid=1000
ARG http_port=8080
ARG agent_port=50000
ARG JENKINS_HOME=/var/jenkins_home

ENV JENKINS_HOME $JENKINS_HOME
ENV JENKINS_SLAVE_AGENT_PORT ${agent_port}

RUN mkdir -p $JENKINS_HOME \
  && chown ${uid}:${gid} $JENKINS_HOME \
  && addgroup -g ${gid} ${group} \
  && adduser -h "$JENKINS_HOME" -u ${uid} -G ${group} -s /bin/bash -D ${user}

VOLUME $JENKINS_HOME

RUN mkdir -p /usr/share/jenkins/ref/init.groovy.d

ARG JENKINS_VERSION
ENV JENKINS_VERSION ${JENKINS_VERSION:-2.164.3}

ARG JENKINS_URL=https://repo.jenkins-ci.org/public/org/jenkins-ci/main/jenkins-war/${JENKINS_VERSION}/jenkins-war-${JENKINS_VERSION}.war
RUN curl -fsSL ${JENKINS_URL} -o /usr/share/jenkins/jenkins.war

ENV JENKINS_UC https://updates.jenkins.io
ENV JENKINS_UC_EXPERIMENTAL=https://updates.jenkins.io/experimental
ENV JENKINS_INCREMENTALS_REPO_MIRROR=https://repo.jenkins-ci.org/incrementals
RUN chown -R ${user} "$JENKINS_HOME" /usr/share/jenkins/ref

EXPOSE ${http_port}

EXPOSE ${agent_port}

ENV COPY_REFERENCE_FILE_LOG $JENKINS_HOME/copy_reference_file.log

USER ${user}

ADD https://raw.githubusercontent.com/jenkinsci/docker/master/jenkins-support /usr/local/bin/jenkins-support
ADD https://raw.githubusercontent.com/jenkinsci/docker/master/jenkins.sh /usr/local/bin/jenkins.sh
ADD https://raw.githubusercontent.com/jenkinsci/docker/master/tini-shim.sh /bin/tini
ENTRYPOINT ["/sbin/tini", "--", "/usr/local/bin/jenkins.sh"]

ADD https://raw.githubusercontent.com/jenkinsci/docker/master/plugins.sh /usr/local/bin/plugins.sh
ADD https://raw.githubusercontent.com/jenkinsci/docker/master/install-plugins.sh /usr/local/bin/install-plugins.sh

USER root
RUN chmod +rwx /usr/local/bin/jenkins-support \
  /usr/local/bin/jenkins.sh \
  /bin/tini \
  /usr/local/bin/plugins.sh \
  /usr/local/bin/install-plugins.sh
RUN ln -s /usr/lib/jvm/java-1.8-openjdk/bin/jar /usr/bin/jar
