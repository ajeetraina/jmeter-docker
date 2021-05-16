FROM ubuntu
LABEL Description="this image is the base ubuntu image which will run with jmeter and all required components"
# updating and installing required packages
RUN apt-get clean && \
        apt-get update && \
        apt-get -qy install \
                        wget \
                        default-jre-headless \
                        telnet \
                        iputils-ping \
                        procps \
                        unzip

# Installing jmeter v4.0, plugins and removing tar/zip files
RUN   mkdir /jmeter \
        && cd /jmeter/ \
        && wget https://archive.apache.org/dist/jmeter/binaries/apache-jmeter-4.0.tgz \
        && tar -xzf apache-jmeter-4.0.tgz \
        && rm apache-jmeter-4.0.tgz \
        && mkdir /jmeter-plugins \
        && cd /jmeter-plugins/ \
        && wget https://jmeter-plugins.org/downloads/file/JMeterPlugins-ExtrasLibs-1.4.0.zip \
        && unzip -o JMeterPlugins-ExtrasLibs-1.4.0.zip -d /jmeter/apache-jmeter-4.0 \
        && cd /jmeter/apache-jmeter-4.0/lib/ext/ \
        && wget https://github.com/NovaTecConsulting/JMeter-InfluxDB-Writer/releases/download/v-1.2/JMeter-InfluxDB-Writer-plugin-1.2.jar
# set jmeter home and add to path in env variables
ENV JMETER_HOME /jmeter/apache-jmeter-4.0/
ENV PATH $JMETER_HOME/bin:$PATH

COPY ./keystore/rmi_keystore.jks /jmeter/apache-jmeter-4.0/bin/rmi_keystore.jks

COPY ./hubPerfTests /root/HubPerfTests
