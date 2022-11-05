# Wordpress Stack using Traefik

Change the values commented (email, domain).

Create a dir in your home named 'traefik' and upload the traefik.yml file provided.
Create another dir named 'letsencrypt' in your home (for certificates).

Persistent volumes are located in /var/lib/docker/volumes/ in your server.

Upload and deploy the stack with docker-compose (docker-compose up -d).

If everything is fine, WordPress, MariaDB and Traefik are up and running.
