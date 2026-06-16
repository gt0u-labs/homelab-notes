# Docker Compose Nginx Test

## Goal

Run a basic Nginx service using Docker Compose and test a simple stop/start troubleshooting flow.

## Environment

* Windows 11 Pro
* WSL Ubuntu
* Docker Desktop
* Docker Compose
* VS Code

## Files

```text
docker-compose.yml
```

## Docker Compose Configuration

```yaml
services:
  nginx:
    image: nginx:latest
    container_name: gt0u-compose-nginx
    ports:
      - "8081:80"
    restart: unless-stopped
```

## Commands Used

```bash
docker compose up -d
docker compose ps
curl -I http://localhost:8081
docker compose logs
docker compose stop
curl -I http://localhost:8081
docker compose start
docker compose ps
curl -I http://localhost:8081
docker compose down
```

## Result

The Nginx container started successfully using Docker Compose.

The service was reachable at:

```text
http://localhost:8081
```

The `curl -I` command returned a successful HTTP response while the container was running.

After stopping the service with:

```bash
docker compose stop
```

the service was no longer reachable.

After starting it again with:

```bash
docker compose start
```

the service responded normally again.

## What I Learned

Docker Compose makes it easier to define and repeat a service configuration.

Instead of writing a long `docker run` command every time, the container settings are saved in a `docker-compose.yml` file.

This lab followed a simple troubleshooting flow:

```text
start service → check status → test response → check logs → stop service → verify failure → start service → verify recovery
```
