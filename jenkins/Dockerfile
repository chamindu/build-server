FROM jenkins/jenkins:lts

USER root

RUN apt-get update
RUN apt-get install -y lsb-release

RUN apt-get install -y apt-transport-https ca-certificates curl software-properties-common

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -

RUN add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"

RUN apt-get update

RUN apt-get install -y docker-ce

RUN usermod -aG docker jenkins

USER jenkins

COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh $(cat /usr/share/jenkins/plugins.txt | tr '\n' ' ')

RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state
