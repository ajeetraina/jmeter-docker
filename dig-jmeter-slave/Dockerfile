FROM images.gcihub.com/dig-basejmeter
LABEL Description="This pulls the jmeter base docker image and exposes the required ports for use as slave node(s)"

# Ports required for JMeter Slaves/Server
EXPOSE 1099 50000

# Application to be executed to start the JMeter container
ENTRYPOINT $JMETER_HOME/bin/jmeter-server \
                        -Dserver.rmi.ssl.keystore.file=/jmeter/apache-jmeter-4.0/bin/rmi_keystore.jks \
                        -Dserver.rmi.localport=50000 \
                        -Dserver_port=1099
