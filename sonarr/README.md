# Docker Sonarr (previously NzbDrone)

### Use
The easiest way to use this is probably a fig file:
```
sonarr:
  image: bybou/sonarr - Installs from Sonarr master repository
  environment:
    - UID=your-own-uid - User with good rights on folder below
    - GID=your-own-gid 
  volumes:
    - /config - Sonarr configuration data files
    - /volumes/completed - Completed downloads from download client
    - /volumes/media - Sonarr media folder
  ports:
    - "8989:8989" - HTTP
    - "9898:9898" - HTTPS
```

### Installation
```sh
$ sudo docker run -d \
 --name sonarr \
 -p 8989:8989 \
 -p 9898:9898 \
 -v /path/to/your/config/folder/:/config \
 -v /path/to/your/media/folder/:/volumes/media \
 -v /path/to/your/completed/downloads:/volumes/completed \
 -e UID=1000 \
 -e GID=1000 \
 --restart always \
 bybou/sonarr
```
From there you can connect to it on:
  - http://127.0.0.1:8989
  - https://127.0.0.1:9898

### Updating
To update successfully, you must configure Sonarr to use the update script in /sonarr-update.sh. This is configured under Settings > (show advanced) > General > Updates > change Mechanism to Script.
After updating, the update script will stop the container.
If the container was run with --restart always, docker will automatically restart Sonarr.
