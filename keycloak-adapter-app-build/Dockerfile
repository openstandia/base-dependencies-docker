FROM maven:3.6.3-jdk-11 as builder

COPY versions.sh /tmp/

COPY pom.xml /tmp/pom.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve

COPY pom-ext.xml /tmp/pom-ext.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom-ext.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve package clean

COPY pom-spring.xml /tmp/pom-spring.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom-spring.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve package clean

