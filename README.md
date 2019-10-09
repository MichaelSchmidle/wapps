# About Wapps

This repository provides the [Docker](https://www.docker.com/) configuration to easily self-host and manage the web apps for my personal use.

# Why Self-host?

There are two reasons why I host the above apps myself:

* Cost: I would pay substantially more for consuming the software as a service than hosting it myself.
* Privacy: I do not entrust the provider with my sensible data.

# Requirements

Wapps requires Docker 17.06.0+ and [Docker Compose](https://docs.docker.com/compose/) 1.14.0+.

# First Usage

To run wapps, 1) create the required Docker network, 2) clone this repository, 3) pre-configure your wapps instance, then 4) spin it up.

```
# 1) Create Docker network ``wapps``
sudo docker network create wapps

# 2) Clone this repository, i.e.:
git clone https://github.com/MichaelSchmidle/wapps

# 3) Copy the file ``default.env`` to ``.env``, open the copied file in a text editor and define the required environment variables, i.e.:
cd wapps
cp default.env .env
nano .env

# 4) Spin up your instance
sudo docker-compose up -d
```
