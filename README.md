# About Wapps

This repository contains the [``docker-compose``](https://docs.docker.com/compose/) files to easily deploy the web apps for my personal use:

| Service | Description | Availability |
| :------ | :---------- | :----------- |
| prxy    | Reverse proxy based on [Traefik](https://traefik.io/) | public |
| dckr    | [Docker]() management GUI based on [Portainer](https://portainer.io/) | public |
| jump    | RDP gateway based on [Guacamole](https://guacamole.apache.org/) | public |
| papr    | Document archive based on [Paperless](https://paperless.readthedocs.io) | private |
| trck    | Website analytics based on [Matomo](https://matomo.org/) | public |

# Requirements

Apart from ``docker-compose`` and its dependencies, this repository currently expects two specific files for the prxy service (i.e. Traefik) to properly work:

* tls.pem: the SSL certificate
* tls.key: the private key for the SSL certificate

A version with support for dynamic certificates from [Let’s Encrypt](https://letsencrypt.org/) is on the to-do list.

# Customization

Most services require customization before they can be deployed. Each service contains one or more ``.default`` files in the respective service folder. Copy those files and rename the copies to match the original file names without ``.default`` (i.e. copy ``.env.default`` to ``.env``), then set the values to fit your needs.
