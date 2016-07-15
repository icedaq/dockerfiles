# Transmission container for the raspberry pi
#
# docker run -d -p 12345:12345 -p 12345:12345/udp \
# 	-p 9091:9091 -v /data/downloads/incomplete:/var/lib/transmission-daemon/incomplete \
#	-v /data/downloads:/var/lib/transmission-daemon/downloads \
#	--name transmission transmission
#

FROM resin/rpi-raspbian:jessie
MAINTAINER Pascal Liniger <pascal.liniger@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y transmission-daemon

ADD files/transmission-daemon /etc/transmission-daemon
ADD files/run_transmission.sh /run_transmission.sh

RUN chown -R debian-transmission: /etc/transmission-daemon && \
chown -R debian-transmission: /run_transmission.sh && \
chmod +x /run_transmission.sh

VOLUME ["/var/lib/transmission-daemon/incomplete"]
VOLUME ["/var/lib/transmission-daemon/downloads"]

EXPOSE 9091
EXPOSE 12345

USER debian-transmission

CMD ["/run_transmission.sh"]
