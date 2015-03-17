# Use latest jboss/base-jdk:7 image as the base
FROM jboss/base-jdk:7

# Set the WILDFLY_VERSION env variable
ENV WILDFLY_VERSION 8.2.0.Final

# Set the CapeDwarf env variable
ENV CAPEDWARF_VERSION 2.0.0.CR6

RUN cd /opt/jboss

# Download & unzip latest CapeDwarf
RUN curl http://download.jboss.org/capedwarf/CapeDwarf_WildFly_$CAPEDWARF_VERSION.zip -o capedwarf_$CAPEDWARF_VERSION.zip
RUN unzip capedwarf_$CAPEDWARF_VERSION.zip -d /opt/jboss
RUN rm /opt/jboss/capedwarf_$CAPEDWARF_VERSION.zip
RUN mv CapeDwarf_WildFly_$CAPEDWARF_VERSION capedwarf

# Set the JBOSS_HOME env variable
ENV JBOSS_HOME /opt/jboss/capedwarf

# Expose the ports we're interested in
EXPOSE 8080

# Set the default command to run on boot
# This will boot CapeDwarf in the standalone mode and bind to all interface
CMD ["/opt/jboss/capedwarf/bin/standalone.sh", "-b", "0.0.0.0", "-c", "standalone-capedwarf-modules.xml"]
