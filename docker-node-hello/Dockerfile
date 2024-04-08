FROM docker.io/node:18.13.0

ARG email="adam@woodford.life"
LABEL "maintainer"=$email
LABEL "rating"="5 Stars" "class"="1st Class"

USER root

ENV AP /data/app
ENV SCRATCH /etc/supervisor/conf.d

RUN apt-get -y update

# daemons
RUN apt-get -y install supervisor
RUN mkdir -p /var/log/supervisor

# supervisor config
COPY ./supervisord/conf.d/* $SCPATH/

# app code
COPY *.js* $AP/

WORKDIR $AP

RUN npm install

CMD ["supervisord", "-n"]
