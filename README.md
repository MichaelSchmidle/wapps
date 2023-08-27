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
| api  | API backend based on [Directus](https://directus.io/) | http (80) redirected to https (443) |
| chat | Open source UI visual tool to build your customized LLM flow based on [Flowise AI](https://flowiseai.com/) | http (80) redirected to https (443) |
| dash | Application dashboard based on [Heimdall](https://heimdall.site/) | http (80) and https (443) redirected to ``HTTPS_MGMT_PORT``<sup>[1](#f1), </sup><sup>[2](#f2)</sup> |
| data | Database management based on [Adminer](https://www.adminer.org/) | http (80) and https (443) redirected to ``HTTPS_MGMT_PORT``<sup>[1](#f1), </sup><sup>[2](#f2)</sup> |
| down | Torrent downloader based on [qBittorrent](https://www.qbittorrent.org/) | http (80) redirected to https (443) |
| dns  | DNS-based ad blocker based on [Pi-hole](https://pi-hole.net/) | http (80) and https (443) redirected to ``HTTPS_MGMT_PORT``<sup>[1](#f1)</sup> |
| get  | Static file server based on [Caddy](https://caddyserver.com/) | http (80) redirected to https (443) |
| home | Home automation based on [Home Assistant]() | http (80) and https (443) redirected to ``HTTPS_MGMT_PORT``<sup>[1](#f1)</sup> |
| jump | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | http (80) redirected to https (443) |
| lib  | Wiki based on [Bookstack](https://www.bookstackapp.com/) | http (80) redirected to https (443) |
| know | Wiki based on [Wiki.js](https://js.wiki/) | http (80) redirected to https (443) |
| pvrm | PVR for movies based on [Radarr](https://radarr.video/) | http (80) redirected to https (443)<sup>[2](#f2)</sup> |
| pvrs | PVR for TV series based on [Sonarr](https://sonarr.tv/) | http (80) redirected to https (443)<sup>[2](#f2)</sup> |
| rms  | Relationship Management System based on [Monica](https://monicahq.com/) | http (80) redirected to https (443)<sup>[2](#f2)</sup> |
| safe | Password manager based on [Passit](https://passit.io/) | http (80) redirected to https (443) |
| sss  | Simple storage service based on [Minio](https://minio.io/) | http (80) redirected to https (443) |
| trck | Website analytics based on [Matomo](https://matomo.org/) | http (80) redirected to https (443) |
| tube | Media downloader based on [AllTube Download](http://alltubedownload.net/) | http (80) redirected to https (443)<sup>[2](#f2)</sup> |

The composition files for each wapp can be found in the ``composition`` folder of this repository.

<sup name="f1">1</sup> ``HTTPS_MGMT_PORT`` refers to the environment variable as defined in the ``.env`` file of your wappster instance. Please refer to the [wappster repository](https://github.com/MichaelSchmidle/wappster) for more instructions.

<sup name="f2">2</sup> This wapp is secured with Single Sign On (SSO) as configured in your wappster instance.

# Wapps Requirements and Usage

To deploy any of the above wapps, use [wappster](https://github.com/MichaelSchmidle/wappster) version 1.2 or higher.
