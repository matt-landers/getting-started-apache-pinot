FROM openjdk:11

WORKDIR /app

ENV PINOT_VERSION=0.8.0

RUN wget https://downloads.apache.org/pinot/apache-pinot-$PINOT_VERSION/apache-pinot-$PINOT_VERSION-bin.tar.gz
RUN tar -zxvf apache-pinot-$PINOT_VERSION-bin.tar.gz

EXPOSE 9000