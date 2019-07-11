FROM jenkinsci/blueocean

ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false -Dhttp.proxyHost=10.155.224.26 -Dhttp.proxyPort=3128 -Dhttps.proxyHost=10.155.224.26 -Dhttps.proxyPort=3128"
ENV HTTP_PROXY="http://10.155.224.26:3128"
ENV HTTPS_PROXY="http://10.155.224.26:3128"

VOLUME jenkins-data:/var/jenkins_home
VOLUME /var/run/docker.sock:/var/run/docker.sock
VOLUME "%HOMEPATH%":/home

COPY security.groovy /usr/share/jenkins/ref/init.groovy.d/security.groovy

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt