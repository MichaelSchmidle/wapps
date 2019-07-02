# About Wapps

This repository contains the [``docker-compose``](https://docs.docker.com/compose/) files to easily self-host the web apps for my personal use.

| Priority    | App    | Description | Availability |
| :---------- | :---   | :---------- | :----------- |
| mandatory   | prxy   | Reverse proxy based on [Traefik](https://traefik.io/) | private |
| recommended | dckr   | [Docker](https://www.docker.com/) management based on [Portainer](https://portainer.io/) as GUI and [Watchtower](https://github.com/| recommended    | data   | Database management based on [Adminer](https://www.adminer.org/) | private |
containrrr/watchtower) as auto-updater | private |
| optional    | ams    | IT asset management system based on [Snipe-IT](https://snipeitapp.com/) | public |
| optional    | beat   | Status page system based on [Cachet](https://cachethq.io/) | public |
| optional    | code   | IDE based on [code-server](https://coder.com/) | public |
| optional    | dev    | Software development & agile management tools based on [Tuleap](https://www.tuleap.org/) | public |
| optional    | dns    | DNS-based ad blocker based on [Pi-hole](https://pi-hole.net/) | public |
| optional    | faas   | Function as a Service based on [IronFunctions](http://open.iron.io/) | public (private GUI) |
| optional    | file   | File browser based on [File Browser](https://filebrowser.github.io/) | public |
| optional    | fin    | Finance manager based on [Firefly III](https://firefly-iii.org/) | public |
| optional    | get    | Static file server based on [Caddy](https://caddyserver.com/) | public |
| optional    | gps    | GPS tracking system based on [Traccar](https://www.traccar.org/) | public |
| optional    | ipam   | IP address management (IPAM) based on [phpipam](https://github.com/pierrecdn/phpipam/) | public |
| optional    | jump   | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | public |
| optional    | know-1 | Wiki based on [Bookstack](https://www.bookstackapp.com/) as alternative to the know app | public |
| optional    | mail   | Webmail based on [Rainloop](https://www.rainloop.net/) | public |
| optional    | meta   | Analytics based on [Metabase](https://www.metabase.com/) | public |
| optional    | papr   | Document archive based on [Paperless](https://paperless.readthedocs.io/) | public |
| optional    | pics   | Photo management based on [Lychee](https://lychee.electerious.com/) | public |
| optional    | pvr-movies | PVR for movies based on [Radarr](https://radarr.video/) | public |
| optional    | pvr-series | PVR for TV series based on [Sonarr](https://sonarr.tv/) | public |
| optional    | pvr-titles | PVR for subtitles based on [Bazarr](https://www.bazarr.media/) | public |
| optional    | safe   | Password manager based on [Bitwarden](https://bitwarden.com/) [compatible server written in Rust](https://github.com/mprasil/bitwarden_rs) | public |
| optional    | srx    | Metasearch engine based on [Searx](https://asciimoo.github.io/searx/) | public |
| optional    | sss    | Simple storage app based on [Minio](https://minio.io/) | public |
| optional    | trck   | Website analytics based on [Matomo](https://matomo.org/) | public |
| optional    | tube   | Media downloader based on [AllTube Download](http://alltubedownload.net/) | public |
| beta        | know-2 | Wiki based on [Wiki.js](https://wiki.js.org/) | public |

# Why Self-host?

There are two reasons why I host the above apps myself:

* Cost: I would pay substantially more for consuming the software as a service than hosting it myself.
* Privacy: I do not entrust the provider with my sensible data.

# Requirements

Apart from ``docker-compose`` and its dependencies (Docker 17.06.0+ and Docker Compose 1.14.0+), this repository requires two conditions to properly work: one regarding SSL certificates, one with regard to Docker networking.

## SSL Certificates

For the time being, the prxy app (i.e. Traefik) works with two HTTPS entry points (public and private) and thus currently relies on two files:

* ``${TRAEFIK_PEM}``: the SSL certificate for your domain
* ``${TRAEFIK_KEY}``: the private key for the SSL certificate

The assumption is that each app runs on its own subdomain and that all apps are covered in the given SSL certificate (the easiest being a wildcard SSL certificate). A version with support for dynamic certificates from [Let’s Encrypt](https://letsencrypt.org/) is on the [to-do list](https://github.com/MichaelSchmidle/wapps/issues/3).

## Docker Networking

Before starting any app, you first need to create the two networks that the apps use. Enter the following two commands:

```
$ sudo docker network create wappsfrontend
$ sudo docker network create wappsbackend
```

Use the flag ``--subnet`` in case you want to define the CIDR notated IP ranges (i.e. ``10.11.12.0/24``) of these two networks.

# Customization

Most apps require customization before they can be deployed. These apps contain one or more ``.default`` files in the respective app folder. Copy those files and rename the copies to match the original file excluding the ``.default`` suffix (i.e. copy ``.env.default`` to ``.env``). Then set the empty variables in the files to fit your needs.

For further instructions, please refer to the ``README.md`` files in the respective app subfolders.

# Usage

To create and run the apps, switch to the corresponding app subfolder (i.e. ``$ cd prxy``) and execute the command ``$ sudo docker-compose up -d``. Please note: The vast majority of apps is only accessible via the prxy app—so make sure to first start the prxy app accordingly.

Apps that are considered publically available (see Availability column in the table above) can be reached over ports ``80`` and ``443``; private apps can be reached over port ``4443``. This gives you the option to limit the traffic to private apps via firewall.
