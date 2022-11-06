# Wordpress stack using Traefik

## Prerequisites

This stack has been tested on Ubuntu Server 22.04 LTS.

Docker and docker-compose plugin have been installed as usual.

## How to use this stack

Change the values commented (email, domain, database fields, etc..).

You may add environment variables (.env). Edit /etc/environment and fill you own ones.

Create a dir in your home named 'traefik' and upload the traefik.yml file provided.

Create another dir named 'letsencrypt' in your home (for certificates).

Persistent volumes are located in /var/lib/docker/volumes/ in your server.

Upload and deploy the stack with docker-compose (docker compose up -d).

If everything is fine, WordPress, MariaDB and Traefik are up and running.
