FROM xataz/alpine:3.3-tini

RUN apk --update add \
      git \
      python

RUN git clone https://github.com/drzoidberg33/plexpy.git /opt/plexpy

VOLUME /data

EXPOSE 8181

WORKDIR /opt/plexpy

CMD ["/usr/bin/tini","--","/usr/bin/python", "PlexPy.py", "--datadir=/data"]
