# About Wapps

This repository contains the [``docker-compose``](https://docs.docker.com/compose/) files to easily deploy the web apps for my personal use:

| App  | Description | Availability |
| :--- | :---------- | :----------- |
| prxy | Reverse proxy based on [Traefik](https://traefik.io/) | public |
| dckr | [Docker](https://www.docker.com/) management GUI based on [Portainer](https://portainer.io/) | private |
| jump | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | public |
| papr | Document archive based on [Paperless](https://paperless.readthedocs.io/) | private |
| trck | Website analytics based on [Matomo](https://matomo.org/) | public |
| git  | Git repository management based on [Gitea](https://gitea.io/en-us/) | private |
| mark | Bookmark and “read it later“ app based on [Wallabag](https://www.wallabag.org/) | public |
| data | Database management based on [Adminer](https://www.adminer.org/) | private |
| sss  | Simple storage app based on [Minio](https://minio.io/) | public |
| meta | Analytics based on [Metabase](https://www.metabase.com/) | private |
| trns | File transfer based on [YouTransfer](http://www.youtransfer.io/) | public |
| fin  | Finance manager based on [Firefly III](https://firefly-iii.org/) | private |
| ipam | IP address management (IPAM) based on [phpipam](https://github.com/pierrecdn/phpipam/) | private |
| home | Application Dashboard based on [Heimdall](https://heimdall.site/) | private |
| get  | Static file server based on [Caddy](https://caddyserver.com/) | public |
| faas | Function as a Service based on [IronFunctions](http://open.iron.io/) | public (private GUI) |
| know | Wiki and blog based on [Confluence](https://www.atlassian.com/software/confluence/) | public |
| dash | Analytics and monitoring based on [Grafana](https://grafana.com/) | private |
| mail | Webmail based on [Rainloop](https://www.rainloop.net/) | public |

# Requirements

Apart from ``docker-compose`` and its dependencies (Docker 17.06.0+ and Docker Compose 1.14.0+), this repository requires two conditions to properly work: one regarding SSL certificates, one with regard to Docker networking.

## SSL Certificates

For the time being, the prxy app (i.e. Traefik) currently relies on two specific files:

* tls.pem: the SSL certificate for your domain
* tls.key: the private key for the SSL certificate

The assumption is that each app runs on its own subdomain and that all apps are covered in the given SSL certificate. A version with support for dynamic certificates from [Let’s Encrypt](https://letsencrypt.org/) is on the to-do list.

## Docker Networking

Before starting any app, you first need to create the two networks that the apps use. Enter the following two commands:

```
$ sudo docker network create wappsfrontend
$ sudo docker network create wappsbackend
```

Use the flag ``--subnet`` in case you want to define the CIDR notated IP ranges (i.e. ``10.11.12.0/24``) of these two networks.

# Customization

Most apps require customization before they can be deployed. These apps contain one or more ``.default`` files in the respective app folder. Copy those files and rename the copies to match the original file excluding the ``.default`` suffix (i.e. copy ``.env.default`` to ``.env``). Then set the empty variables in the files to fit your needs.

Apps that are considered publically available (see Availability column in the table above) can be reached over ports ``80`` and ``443``; private apps can be reached over port ``4443``. This gives you the option to limit the traffic to private apps via firewall.

For further instructions, please refer to the ``README.md`` files in the respective app subfolders.
