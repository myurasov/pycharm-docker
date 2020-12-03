FROM ubuntu:focal

# common packages
RUN apt-get update
RUN apt-get install -y wget

# python
RUN apt-get install -y python3 python3-pip
RUN pip3 install --upgrade pip

# install pycharm
ARG PYCHARM_SOURCE=https://download.jetbrains.com/python/pycharm-community-2020.3.tar.gz
RUN wget -q --show-progress --progress=bar:force:noscroll -O pycharm.tar.gz $PYCHARM_SOURCE
RUN mkdir -p /opt/pycharm && mv pycharm.tar.gz /opt/pycharm
RUN cd /opt/pycharm && tar --strip-components=1 -xzf pycharm.tar.gz && rm pycharm.tar.gz

# copy config files
COPY ./res /

# cleanup
# RUN rm -rf /var/lib/apt/lists/*

VOLUME /project
WORKDIR /project

CMD ["sh", "/opt/pycharm/bin/pycharm.sh"]
