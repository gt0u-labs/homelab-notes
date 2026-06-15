# Docker Nginx Service Test

## Goal

Test Docker inside WSL by running a simple Nginx container, checking if it responds, stopping it, and starting it again.

I had used Docker/Nginx before in other personal setups, but this was a small documented lab for my homelab notes.

## Environment

* Windows 11 Pro
* WSL Ubuntu
* Docker Desktop
* Docker Desktop WSL Integration
* PowerShell 7
* VS Code

## Problem

At first, Docker was not available inside my Ubuntu WSL distro.

```bash
docker --version
```

The terminal suggested enabling Docker Desktop WSL integration.

I checked WSL from PowerShell:

```powershell
wsl -l -v
```

Ubuntu and `docker-desktop` were both running on WSL2, so the issue was Docker integration, not WSL itself.

## Fix

I enabled Ubuntu integration from Docker Desktop:

```text
Settings → Resources → WSL Integration → Enable Ubuntu → Apply & Restart
```

After restarting the terminal, Docker worked inside WSL.

## Commands Used

```bash
docker --version
docker compose version

docker run -d --name gt0u-nginx -p 8080:80 nginx
docker ps
curl -I http://localhost:8080
docker logs gt0u-nginx

docker stop gt0u-nginx
curl -I http://localhost:8080

docker start gt0u-nginx
docker ps
curl -I http://localhost:8080

docker rm -f gt0u-nginx
```

## Result

Nginx loaded correctly at:

```text
http://localhost:8080
```

After stopping the container, the service was no longer reachable.

After starting it again, the service responded again.

## What I Learned

Docker Desktop can expose Docker commands inside WSL, but WSL integration must be enabled for the Ubuntu distro.

This was a basic lab, but it followed a real troubleshooting flow:

```text
problem → check → fix → verify
```
