FROM openjdk:11

WORKDIR /app

ENV PINOT_VERSION=0.7.1

RUN wget https://downloads.apache.org/pinot/apache-pinot-incubating-$PINOT_VERSION/apache-pinot-incubating-$PINOT_VERSION-bin.tar.gz
RUN tar -zxvf apache-pinot-incubating-$PINOT_VERSION-bin.tar.gz

EXPOSE 9000