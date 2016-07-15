# jekyll
#
# docker run --name jekyll -v $DATADIR/jekyll:/src -d jekyll serve
#

FROM ruby:latest

MAINTAINER Pascal Liniger <pascal.liniger@gmail.com>

RUN apt-get update \
	&& apt-get install -y \
		node \
		python-pygments \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/

RUN gem install \
	github-pages \
	jekyll \
	jekyll-redirect-from \
	kramdown \
	rdiscount \
	rouge

VOLUME /src

EXPOSE 9001

WORKDIR /src

ENTRYPOINT ["jekyll"]
