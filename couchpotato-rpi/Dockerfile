# Couchpotato for the raspberry pi
#
# docker run -d -p 5050:5050 \
# 	-v /data/couchpotato/couchpotato:/root/.couchpotato
#	 --name couchpotato couchpotato
#

FROM resin/rpi-raspbian:jessie

MAINTAINER Pascal Liniger <pascal.liniger@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -qq update \
	&& apt-get -qq upgrade \
	&& apt-get install -qq python git

RUN git clone https://github.com/RuudBurger/CouchPotatoServer.git /couchpotato

VOLUME /root/.couchpotato

EXPOSE 5050

ENTRYPOINT python /couchpotato/CouchPotato.py
