FROM jenkins:1.642.1

# Install plugins
COPY config/plugins.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt

# Copy security setup
COPY config/setup-security.groovy /usr/share/jenkins/ref/init.groovy.d/setup-security.groovy

# Copy jobs
COPY jobs/gradame-api/config.xml /usr/share/jenkins/ref/jobs/gradame-api/config.xml
