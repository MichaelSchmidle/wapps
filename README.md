# About Wapps

This repository contains the [``docker-compose``](https://docs.docker.com/compose/) files to easily deploy the web apps for my personal use:

| Service | Description | Availability |
| :------ | :---------- | :----------- |
| prxy    | Reverse proxy based on [Traefik](https://traefik.io/) | public |
| dckr    | [Docker](https://www.docker.com/) management GUI based on [Portainer](https://portainer.io/) | private |
| jump    | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | public |
| papr    | Document archive based on [Paperless](https://paperless.readthedocs.io) | private |
| trck    | Website analytics based on [Matomo](https://matomo.org/) | public |
| git     | Git repository management based on [Gitea](https://gitea.io/en-us/) | private |
| mark    | Bookmark and “read it later“ service based on [Wallabag](https://www.wallabag.org/) | public |
| data    | Database management based on [Adminer](https://www.adminer.org/) | private |
| sss     | Simple storage service based on [Minio](https://minio.io/) | public |
| meta    | Analytics based on [Metabase](https://www.metabase.com/) | private |
| trns    | File transfer based on [YouTransfer](http://www.youtransfer.io/) | public |
| fin     | Finance manager based on [Firefly III](https://firefly-iii.org/) | private |
| ipam    | IP address management (IPAM) based on [phpipam](https://github.com/pierrecdn/phpipam) | private |
| home    | Application Dashboard based on [Heimdall](https://heimdall.site/) | public |

# Requirements

Apart from ``docker-compose`` and its dependencies, this repository requires two conditions to properly work: one regarding SSL certificates, one with regard to Docker networking.

## SSL Certificates

For the time being, the prxy service (i.e. Traefik) currently relies on two specific files:

* tls.pem: the SSL certificate for your domain
* tls.key: the private key for the SSL certificate

The assumption is that each service runs on its own subdomain and that all services are covered in the given SSL certificate. A version with support for dynamic certificates from [Let’s Encrypt](https://letsencrypt.org/) is on the to-do list.

## Docker Networking

Before starting any service, you first need to create the two networks that the services use. Enter the following two commands:

```
$ sudo docker network create wapps_frontends
$ sudo docker network create wapps_backends
```

# Customization

Most services require customization before they can be deployed. These services contain one or more ``.default`` files in the respective service folder. Copy those files and rename the copies to match the original file excluding the ``.default`` suffix (i.e. copy ``.env.default`` to ``.env``). Then set the values to fit your needs.

Services that are considered publically available (see Availability column in the table above) can be reached over ports ``80`` and ``443``; private services can be reached over port ``4443``. This gives you the option to limit the traffic to private services via firewall.

For further instructions, please refer to the ``README.md`` files in the respective service subfolders.
