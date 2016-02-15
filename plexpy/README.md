
# PlexPy Docker Image

[![](https://badge.imagelayers.io/webdestroya/plexpy:latest.svg)](https://imagelayers.io/?images=webdestroya/plexpy:latest 'Get your own badge on imagelayers.io')

This is a lightweight container that runs [PlexPy](https://github.com/drzoidberg33/plexpy), a web-based monitoring and tracking tool for Plex Media Server.

## Volumes
* `/data` - This volume is used to store the database and configuration file for PlexPy.

## Usage

```
docker run -d --name plexpy \
  -p 8181:8181 \
  -v /etc/docker/data:/data \
  -v /PLEXLOGS:/logs \
  webdestroya/plexpy
```

To update to the latest version of plexpy, just recreate the container.
