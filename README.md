# User Guide for Traefik + WordPress Stack

This document provides instructions for deploying a WordPress stack with MariaDB using Docker Compose, managed with Traefik as a reverse proxy and SSL certificate manager.

## Prerequisites
- Docker and Docker Compose installed on the system.
- A valid domain pointing to the server's IP address.
- SSL certificates automatically generated with Let's Encrypt.

## Project Structure
The stack consists of the following files:
- `.env` → Contains environment variables such as database credentials and domain configuration.
- `docker-compose.yml` → Defines the WordPress, MariaDB, and Traefik services.
- `traefik.toml` → Traefik configuration.

## Configuration
### 1. Edit the `.env` file
Define values for the domain and database credentials:
```ini
DOMAIN=mydomain.com
ROUTER=wordpress
DB_USER=user
DB_PASSWORD=password
DB_NAME=wordpress_db
```
> **Note:** Replace `mydomain.com` with your actual domain.

### 2. Edit `traefik.toml`
Make sure to update the email for SSL certificates:
```toml
[certificatesResolvers.myresolver.acme]
  email = "your-email@example.com"
```
This email should match the one in `docker-compose.yml`.

### 3. Start the services
Run the following command to start the stack:
```sh
docker-compose up -d
```
This will run the containers in the background.

## Accessing WordPress
Once the stack is running, access WordPress in your browser at:
```
https://mydomain.com
```

## Managing Traefik
If you want to access the Traefik dashboard, enable it by adding the `--api.dashboard=true` option in `docker-compose.yml` and visit:
```
http://mydomain.com:8080
```

## Data Persistence
WordPress and database data are stored in the following volumes:
- `./wordpress` → Contains WordPress files.
- `./db` → Contains the MariaDB database.

## Stopping the Stack
To stop the containers without removing volumes:
```sh
docker-compose down
```
To remove volumes and delete all stored data:
```sh
docker-compose down -v
```
> **Warning:** Deleting volumes will erase all data.

## Troubleshooting
### Viewing Service Logs
To debug container errors, check logs with:
```sh
docker-compose logs -f
```
For a specific service, use:
```sh
docker-compose logs -f traefik
```

## Summary
This stack provides a self-hosted solution for WordPress with Traefik as a reverse proxy and automated SSL certificates. Be sure to keep services updated and periodically check logs to prevent issues.

