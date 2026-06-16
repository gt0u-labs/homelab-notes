# Incident Report: Nginx Monitoring Test

## Summary

I tested a basic service outage and recovery flow using Docker Compose, Nginx and Uptime Kuma.

The idea was simple: run a Nginx service, monitor it, stop it on purpose, check if the monitor detects the outage, then start it again and verify recovery.

## Environment

* Windows 11 Pro
* WSL Ubuntu
* Docker Desktop
* Docker Compose
* Nginx
* Uptime Kuma

## Services

```text
Nginx: http://localhost:8090
Uptime Kuma: http://localhost:3001
Monitor URL: http://nginx:80
```

## What I Did

First, I started the Docker Compose stack and checked that both Nginx and Uptime Kuma were running.

Then I added a monitor in Uptime Kuma for the Nginx service.

After confirming that the service was UP, I stopped only the Nginx container:

```bash
docker compose stop nginx
```

Uptime Kuma detected the service as DOWN.

Then I started Nginx again:

```bash
docker compose start nginx
```

After a short moment, Uptime Kuma detected the service as UP again.

## Verification

I checked the service from the terminal with:

```bash
curl -I http://localhost:8090
```

I also used Uptime Kuma to confirm the UP, DOWN and recovered states.

Screenshots are saved in the `screenshots` folder.

## What I Learned

This helped me understand a simple monitoring flow:

```text
service running -> service down -> monitor detects issue -> service restored -> monitor confirms recovery
```

I also learned that Uptime Kuma should use `http://nginx:80` because both services are running inside the same Docker Compose network.
