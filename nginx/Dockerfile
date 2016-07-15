# Simple nginx with ssl
#
# docker run --name webdav -p 9003:9003 \ 
# 	-v /data/webdav/config:/etc/nginx/sites-enabled \
#	-v /data/webdav/ssl:/etc/nginx/certs -v \
#	-v /data/webdav/data:/var/www/html -d webdav
#

FROM dockerfile/ubuntu

# Install Nginx.
RUN \
  add-apt-repository -y ppa:nginx/stable && \
  apt-get update && \
  apt-get install -y nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx

# Define mountable directories.
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

# Define working directory.
WORKDIR /etc/nginx

# Define default command.
CMD ["nginx"]

# Expose ports.
EXPOSE 9003
# EXPOSE 443
