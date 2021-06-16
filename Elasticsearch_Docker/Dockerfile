##
#
# Dockerfile for our Elastic Search cluster.  The dockerfile is based off of
#  https://github.com/dockerfile/elasticsearch.
#

# Pull base image.
FROM ubuntu:14.04

ENV ES_PKG_NAME elasticsearch-1.4.2

# Install system level packages needed to install elastic search or dependancies.
RUN apt-get -y install software-properties-common

# Install Java.
RUN  apt-get update && \
     apt-get install default-jdk -y
# Define commonly used JAVA_HOME variable
# ENV JAVA_HOME /usr/lib/jvm/java8-oracle

# Install Elasticsearch.
RUN \
    cd / && \
    apt-get install wget -y && \
    apt-get update && \
    wget https://download.elasticsearch.org/elasticsearch/elasticsearch/$ES_PKG_NAME.tar.gz && \
    tar xvzf $ES_PKG_NAME.tar.gz && \
    rm -f $ES_PKG_NAME.tar.gz && \
    mv /$ES_PKG_NAME /elasticsearch

# Mount elasticsearch.yml config
ADD elasticsearch.yml /elasticsearch/config/elasticsearch.yml
CMD ["/elasticsearch/bin/elasticsearch"]
# Expose ports.

EXPOSE 9200
#EXPOSE 9300


