![wapps logo](https://cdn.jsdelivr.net/gh/MichaelSchmidle/wapps/logo.svg)

# About Wapps

Wapps is the abbreviation for self-hosted “web apps” that can be easily deployed and managed with [wappster](https://github.com/MichaelSchmidle/wappster).

This repository contains the assets for wapps:
* the wapps logo
* the wapps catalogue
* the wapps composition files

# Why Self-host?

There are three reasons for self-hosting:

* Availability: Required functionality not being available as managed services.
* Cost: Paying substantially more for consuming the software as a service than self-hosting it.
* Privacy: Not entrusting the provider with sensible data.

# Wapps Catalogue

| Wapp | Description | Port |
| :--- | :---------- | :--- |
| api  | API backend based on [Strapi](https://strapi.io/) | http (80) redirected to https (443) |
| data | Database management based on [Adminer](https://www.adminer.org/) | http (80) and https (443) redirected to ``HTTPS_MGMT_PORT``<sup name="r1">[1](#f1)</sup> |
| dns  | DNS-based ad blocker based on [Pi-hole](https://pi-hole.net/) | http (80) and https (443) redirected to ``HTTPS_MGMT_PORT``<sup name="r1">[1](#f1)</sup> |
| get  | Static file server based on [Caddy](https://caddyserver.com/) | http (80) redirected to https (443) |
| jump | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | http (80) redirected to https (443) |
| know | Wiki based on [Bookstack](https://www.bookstackapp.com/) | http (80) redirected to https (443) |
| pvrm | PVR for movies based on [Radarr](https://radarr.video/) | http (80) redirected to https (443) |
| pvrs | PVR for TV series based on [Sonarr](https://sonarr.tv/) | http (80) redirected to https (443) |
| safe | Password manager based on [Passit](https://passit.io/) | http (80) redirected to https (443) |
| sss  | Simple storage app based on [Minio](https://minio.io/) | http (80) redirected to https (443) |
| trck | Website analytics based on [Matomo](https://matomo.org/) | http (80) redirected to https (443) |
| tube | Media downloader based on [AllTube Download](http://alltubedownload.net/) | http (80) and https (443) redirected to ``HTTPS_MGMT_PORT``<sup name="r1">[1](#f1)</sup> |

The composition files for each wapp can be found in the ``composition`` folder of this repository.

<sup><a name="f1" href="#r1">1</a></sup> ``HTTPS_MGMT_PORT`` refers to the environment variable as defined in the ``.env`` file of your wappster instance. Please refer to the [wappster repository](https://github.com/MichaelSchmidle/wappster) for more instructions.

# Wapps Usage

To deploy any of the above wapps, use [wappster](https://github.com/MichaelSchmidle/wappster).
