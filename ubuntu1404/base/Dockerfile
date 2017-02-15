FROM ubuntu:14.04.4
MAINTAINER Jochen Breuer "basalt@dajool.com"

RUN apt-get update
RUN apt-get -y dist-upgrade
RUN apt-get -y install wget curl add-apt-key
RUN wget http://pelicanbay.de/pool/main/p/pelicanbay-apt-repository/pelicanbay-apt-repository_0.1_all.deb
RUN dpkg -i pelicanbay-apt-repository_0.1_all.deb
RUN apt-get update && apt-get install -y basalt

WORKDIR /src
CMD ["/bin/bash"]
