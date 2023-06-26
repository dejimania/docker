FROM docker.io/node:18.13.0

ARG email="kayluv09@yahoo.com"
LABEL "maintainer"=$email
LABEL "rating"="Five starts" "class"="First Class"

USER root

ENV AP /data/app
ENV SCPATH /etc/supervisor/conf.d

RUN apt-get -y update

# Deamons
RUN apt-get -y install supervisor
RUN mkdir -p /var/log/supervicor

# Supervisor Config
COPY ./supervisord/conf.d/* $SCPATH/

# APP Code
COPY *.js* $AP/

WORKDIR $AP

RUN npm install

CMD ["supervisord", "-n"]
