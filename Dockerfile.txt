FROM tomcat

MAINTAINER sanjeeb

RUN apt-get update && apt-get -y upgrade

WORKDIR /usr/local/tomcat
