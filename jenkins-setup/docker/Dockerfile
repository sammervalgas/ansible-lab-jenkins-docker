FROM jenkins/jenkins:lts

ARG JENKINS_ADMIN_USER=admin
ARG JENKINS_ADMIN_PASS=admin
ARG JENKINS_HOME=/var/jenkins_home
ARG JENKINS_URL=http://localhost:8080

ENV JENKINS_ADMIN_USER=${JENKINS_ADMIN_USER}
ENV JENKINS_ADMIN_PASS=${JENKINS_ADMIN_PASS}
ENV JENKINS_HOME=${JENKINS_HOME}
ENV JENKINS_URL=${JENKINS_URL}
#    RELOAD_CASC=true
ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"


COPY jenkins/init.groovy.d /usr/share/jenkins/ref/init.groovy.d/

RUN echo $JENKINS_VERSION | tee \
    /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state \
    /usr/share/jenkins/ref/jenkins.install.InstallUtil.lastExecVersion

USER root

RUN apt-get update && apt-get install -y wget

VOLUME $JENKINS_HOME
