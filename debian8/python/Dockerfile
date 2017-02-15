FROM basaltbuild/debian8_base:latest
MAINTAINER Jochen Breuer "basalt@dajool.com"

RUN apt-get update
RUN apt-get -y dist-upgrade
RUN apt-get update && apt-get install -y build-essential python-pip python-dev python-virtualenv libjpeg-dev libjpeg62-turbo-dev libpng12-dev libwebp-dev
RUN pip install virtualenv-tools

WORKDIR /src
CMD ["/bin/bash"]
