FROM mizzouceri/tomcat-mvn-java11:V1
MAINTAINER Songjie Wang "wangso@missouri.edu"

# Fix Debian repository issues
FROM mizzouceri/tomcat-mvn-java11:V1

RUN printf '%s\n' \
    'deb [trusted=yes] http://archive.debian.org/debian buster main' \
    'deb [trusted=yes] http://archive.debian.org/debian-security buster/updates main' \
    > /etc/apt/sources.list \
    && apt-get -o Acquire::Check-Valid-Until=false update \
    && apt-get -y install --no-install-recommends lsb-release net-tools nano \
    && rm -rf /var/lib/apt/lists/*
RUN apt-get -y install default-mysql-server maven

RUN mkdir -p /usr/local/tomcat/webapps/ROOT/js
COPY Covid19-website/src/main/resources/static/js/ng-table.js /usr/local/tomcat/webapps/ROOT/js/
COPY Covid19-website/target/*.war /usr/local/tomcat/webapps/ROOT.war
WORKDIR /root 
ADD Covid19-website /root/Covid19-website

WORKDIR /root/Covid19-website


# RUN mvn clean package
# RUN cp /root/Covid19-website/target/*.war /usr/local/tomcat/webapps/
# RUN cp Covid19-website/src/main/resources/static/js/ng-table.js /usr/local/tomcat/webapps/ROOT/js/
