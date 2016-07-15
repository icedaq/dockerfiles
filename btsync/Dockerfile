# Run btsync in container.
#
# docker run -d -v /data/sync:/mnt/sync \
#	-p 8888:8888 -p 55555 \
#	--name btsync \
#	btsync

FROM frolvlad/alpine-glibc
MAINTAINER Pascal Liniger <pascal.liniger@gmail.com>

ADD https://download-cdn.getsync.com/stable/linux-x64/BitTorrent-Sync_x64.tar.gz /tmp/sync.tar.gz
RUN tar -xf /tmp/sync.tar.gz -C /usr/sbin \
	&& rm -f /tmp/sync.tar.gz

COPY btsync.conf /etc/
COPY run_sync /opt/

EXPOSE 8888
EXPOSE 55555

VOLUME /mnt/sync

ENTRYPOINT ["/opt/run_sync"]
CMD ["--log", "--config", "/etc/btsync.conf"]
