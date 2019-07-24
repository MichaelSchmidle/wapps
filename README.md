# About Wapps

This repository contains the [``docker-compose``](https://docs.docker.com/compose/) files to easily self-host the web apps for my personal use.

## Mandatory Apps

The following apps are mandatory to run wapps:

| App  | Description | Availability |
| :--- | :---------- | :----------- |
| prxy | Reverse proxy based on [Traefik](https://traefik.io/) | private |

## Recommended Apps

For added convenience in securing and managing wapps, I recommend also deploying the following apps:

| App  | Description | Availability |
| :--- | :---------- | :----------- |
| ssl  | Automatic generation and renewal of Let's Encrypt wildcard SSL certificate based on [docker-letsencrypt-dns](https://github.com/adferrand/docker-letsencrypt-dns) | N/A |
| dckr | [Docker](https://www.docker.com/) management based on [Portainer](https://portainer.io/) as GUI and [Watchtower](https://github.com/containrrr/watchtower) as auto-updater | private |
| data | Database management based on [Adminer](https://www.adminer.org/) | private |

## Optional Apps

Listed below are the web apps that give this repository its name wapps. It’s possible to deploy just any single one or all of these – that’s entirely up to you.

| App  | Description | Availability |
| :--- | :---------- | :----------- |
| dns  | DNS-based ad blocker based on [Pi-hole](https://pi-hole.net/) | public |
| fast | HTML5 speedtest based on [Speedtest](https://www.github.com/adolfintel/speedtest) | public |
| get  | Static file server based on [Caddy](https://caddyserver.com/) | public |
| gps  | GPS tracking system based on [Traccar](https://www.traccar.org/) | public |
| ipam | IP address management (IPAM) based on [phpipam](https://github.com/pierrecdn/phpipam/) | public |
| jump | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | public |
| know | Wiki based on [Bookstack](https://www.bookstackapp.com/) as alternative to the know app | public |
| mail | Webmail based on [Rainloop](https://www.rainloop.net/) | public |
| pics | Photo management based on [Lychee](https://lychee.electerious.com/) | public |
| pvr-movies | PVR for movies based on [Radarr](https://radarr.video/) | public |
| pvr-series | PVR for TV series based on [Sonarr](https://sonarr.tv/) | public |
| pvr-titles | PVR for subtitles based on [Bazarr](https://www.bazarr.media/) | public |
| safe | Password manager based on [Bitwarden](https://bitwarden.com/) [compatible server written in Rust](https://github.com/mprasil/bitwarden_rs) | public |
| sss  | Simple storage app based on [Minio](https://minio.io/) | public |
| trck | Website analytics based on [Matomo](https://matomo.org/) | public |
| tube | Media downloader based on [AllTube Download](http://alltubedownload.net/) | public |

## Beta Apps

The following apps are still in beta; yet I want to test them as part of my wapps:

| App  | Description | Availability |
| :----| :---------- | :----------- |
| know-beta | Wiki based on [Wiki.js](https://wiki.js.org/) | public |

# Why Self-host?

There are two reasons why I host the above apps myself:

* Cost: I would pay substantially more for consuming the software as a service than hosting it myself.
* Privacy: I do not entrust the provider with my sensible data.

# Requirements

Apart from ``docker-compose`` and its dependencies (Docker 17.06.0+ and Docker Compose 1.14.0+), this repository requires two conditions to be met: one regarding SSL certificates, one with regard to Docker networking.

## SSL Certificates

The assumption is that each app runs on its own subdomain and that all apps are covered in the given SSL certificate (the easiest being a wildcard SSL certificate).

Wapps uses two HTTPS entry points: the regular one over port 443 for most apps and the custom port 4443 to provide added security to management interfaces. This allows to lock down port 4443 via firewall. At the moment, the prxy app (i.e. Traefik) unfortunatley only supports Let's Encrypt certificates for a single entry point (see [corresponding issue](https://github.com/MichaelSchmidle/wapps/issues/3)).

This requires that you either A) use the ssl companion app or B) provide your own certificate/s.

### Ssl Companion App

The easiest way to secure your apps with SSL is to have the ssl app generate/renew a fitting wildcard certificate. The app is designed to provide domain validation via DNS.

As for all other apps, copy the ``.env.default`` file to ``.env`` inside the app folder and provide the necessary configuration in the copied file. Additionally, edit the ``domains.conf`` file of the ssl app by replacing the string ``DOMAIN`` according to your wildcard domain like ``*.example.org``. Then simply start the app by execitung ``docker-compose up -d``. (Note: Do not remove the trailing string ``autorestart-containers=wappsprxy_traefik_1``!)

### Bring Your Own Certificate

Alternatively, you can use a custom certificate. Configure the path to the certificate and private key in the ``.env`` file of the prxy app:

* ``${TRAEFIK_PEM}``: the SSL certificate for your domain
* ``${TRAEFIK_KEY}``: the private key for the SSL certificate

## Docker Networking

Before starting any app, you first need to create the two networks that the apps use. Enter the following two commands:

```
$ sudo docker network create wapps_frontend
$ sudo docker network create wapps_backend
```

Use the flag ``--subnet`` in case you want to define the CIDR notated IP ranges (i.e. ``10.11.12.0/24``) of these two networks.

# Customization

Most apps require customization before they can be deployed. These apps contain one or more ``.default`` files in the respective app folder. Copy those files and rename the copies to match the original file excluding the ``.default`` suffix (i.e. copy ``.env.default`` to ``.env``). Then set the empty variables in the files to fit your needs.

For further instructions, please refer to the ``README.md`` files in the respective app subfolders.

# Usage

To create and run the apps, switch to the corresponding app subfolder (i.e. ``$ cd prxy``) and execute the command ``$ sudo docker-compose up -d``. Please note: The apps are only accessible via the prxy app—so make sure to first provide the necessary SSL certificates and then start the prxy app accordingly.

Apps that are considered publically available (see Availability column in the table above) can be reached over ports ``80`` and ``443``; private apps can be reached over port ``4443``. This gives you the option to limit the traffic to private apps via firewall.
