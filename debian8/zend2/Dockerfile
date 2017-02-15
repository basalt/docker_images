FROM basaltbuild/debian8_base:latest
MAINTAINER Jochen Breuer "basalt@dajool.com"

RUN apt-get update
RUN apt-get -y dist-upgrade
RUN apt-get update && apt-get install -y build-essential php5-cli git curl

WORKDIR /src
CMD ["/bin/bash"]
