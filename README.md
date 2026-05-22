# Content Acquirer Service

I do not claim responsibility or association with the creation of the docker images used in the included docker compose file.  The included file and service definition just serve as a template to help others setup their own media management software.  All rights and credit for the Docker images and their underlying software should go to those who helped contribute to make the radarr, sonarr, prowlarr and pia-qbittorrent possible.

## Requirements

* Docker v20+
* Docker compose plugin

## Installation

### docker-compose.yml
You can spin up the containers by simply running `docker compose up` from the project directory.  However, the mounted directories and VPN configuration in the docker-compose file are specific to my needs, so it is recommended that you update accordingly.

### docker-compose@.service

* Copy or symlink the included systemd service definition to `/etc/systemd/system/`
* Run `systemctl enable docker-compose@acquire-content.service`
	* This registers the service to be started on boot, so feel free to skip if that's not what you want.
* Run `systemctl start docker-compose@acquire-content.service`
	* This starts the docker compose file as a service.

## Configuration

### docker-compose.yml

* In the compose file you'll see a number of environmental variables called `PUID` and `PGID`. This is the user id and group id to use for all files touch by the running containers.  These values must be provided to avoid unexpected permission issues.
	* If you just want to use your login user and group for these you can check what they are with the `id $(whoami)` command. You should see `uid=` and a `gid=` the number in each of these cases is what you want to set `PUID` and `PGID` to respectively.
* The volume mounts configured in the compose file are highly specific to my needs, so you'll need to update each of these as needed.  It is highly suggested that you have a shared volume for the download client (transmission_and_openvpn) and whatever your media client uses.  For more details see the write up here: https://wiki.servarr.com/docker-guide#consistent-and-well-planned-paths
	* This is why in the docker-compose.yml you'll see a shared volume called `host_data`.



### docker-compose@.service
