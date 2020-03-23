FROM maven:3.6.3-jdk-11 as builder

COPY versions.sh /tmp/

COPY pom.xml /tmp/pom.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:go-offline

COPY pom-ext.xml /tmp/pom-ext.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom-ext.xml -s /usr/share/maven/ref/settings-docker.xml dependency:go-offline package clean

COPY pom-jar.xml /tmp/pom-jar.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom-jar.xml -s /usr/share/maven/ref/settings-docker.xml dependency:go-offline package clean

COPY pom-war.xml /tmp/pom-war.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom-war.xml -s /usr/share/maven/ref/settings-docker.xml dependency:go-offline package clean

COPY pom-ear.xml /tmp/pom-ear.xml
RUN . /tmp/versions.sh && mvn -B -f /tmp/pom-ear.xml -s /usr/share/maven/ref/settings-docker.xml dependency:go-offline package clean

