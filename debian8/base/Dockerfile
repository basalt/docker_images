FROM debian:8
MAINTAINER Jochen Breuer "basalt@dajool.com"

RUN apt-get update \
 && apt-get -y dist-upgrade
RUN apt-get -y install python-pip ruby ruby-dev
RUN pip install basalt-tasks \
 && gem install fpm

WORKDIR /src
CMD ["/bin/bash"]
