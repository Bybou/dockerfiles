FROM xataz/alpine:3.3-tini
MAINTAINER bybou <https://github.com/bybou>

ENV UID=1000 GID=1000

RUN echo "@testing http://dl-4.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories && \	
	apk add -U curl-dev mono@testing && \
	jack_tag=$(curl -sX GET  "https://api.github.com/repos/Jackett/Jackett/releases/latest" | awk '/tag_name/{print $4;exit}' FS='[""]') && \
	mkdir -p /opt && cd /opt && wget https://github.com/Jackett/Jackett/releases/download/$jack_tag/Jackett.Binaries.Mono.tar.gz && \
	tar xzf Jackett.Binaries.Mono.tar.gz && rm -rf /opt/*.tar.gz /var/cache/apk/*

EXPOSE 5000

ADD startup /usr/bin/startup
RUN chmod +x /usr/bin/startup

CMD ["/usr/bin/tini","--","startup"]
