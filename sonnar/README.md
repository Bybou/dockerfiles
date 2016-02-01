Docker Sonarr (previously NzbDrone)

Ports
TCP 8989 - Web Interface

Volumes
/volumes/config - Sonarr configuration data
/volumes/completed - Completed downloads from download client
/volumes/media - Sonarr media folder

Running
sudo docker run -d --name sonarr -p 8989:8989 -p 9898:9898 -v /path/to/your/media/folder/:/volumes/media -v /path/to/your/completed/downloads:/volumes/completed tuxeh/sonarr -e UID=1000 -e GID=1000 --restart always bybou/sonarr

Updating
To update successfully, you must configure Sonarr to use the update script in /sonarr-update.sh. This is configured under Settings > (show advanced) > General > Updates > change Mechanism to Script.
After updating, the update script will stop the container. If the container was run with --restart always, docker will automatically restart Sonarr.
