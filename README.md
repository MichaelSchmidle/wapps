# About Wapps

Wapps is the abbreviation for self-hosted “web apps” that can be easily deployed and managed with [Wappster](https://github.com/MichaelSchmidle/wappster).

This repository contains the assets for wapps:
* the wapps logo
* the wapps catalogue
* the wapps composition files

# Why Self-host?

There are two reasons why I want to host below listed wapps myself:

* Cost: I would pay substantially more for consuming the software as a service than hosting it myself.
* Privacy: I do not entrust the provider with my sensible data.

# Wapps Catalogue

| Wapp  | Description | Port |
| :--- | :---------- | :----------- |
| data | Database management based on [Adminer](https://www.adminer.org/) | ``HTTPS_MGMT_PORT``<sup name="r1">[1](#f1)</sup> |
| dns  | DNS-based ad blocker based on [Pi-hole](https://pi-hole.net/) | 80, 4443 |
| get  | Static file server based on [Caddy](https://caddyserver.com/) | 80, 4443 |
| gps  | GPS tracking system based on [Traccar](https://www.traccar.org/) | 80, 4443 |
| ipam | IP address management (IPAM) based on [Netbox](https://github.com/netbox-community/netbox) | 80, 4443 |
| jump | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | 80, 4443 |
| know | Wiki based on [Bookstack](https://www.bookstackapp.com/) | 80, 4443 |
| pvr-movies | PVR for movies based on [Radarr](https://radarr.video/) | 80, 4443 |
| pvr-series | PVR for TV series based on [Sonarr](https://sonarr.tv/) | 80, 4443 |
| sss  | Simple storage app based on [Minio](https://minio.io/) | 80, 4443 |
| trck | Website analytics based on [Matomo](https://matomo.org/) | 80, 4443 |
| tube | Media downloader based on [AllTube Download](http://alltubedownload.net/) | 80, 4443 |

The composition files for each wapp can be found in the ``wapps-composition`` folder of this repository.

<a name="f1" href="#r1">1</a> ``HTTPS_MGMT_PORT`` refers to the environment variable as defined in the ``.env`` file of your wapps instance. Please refer to the [wapps repository](https://github.com/MichaelSchmidle/wapps) for more information.

# Wapps Usage


