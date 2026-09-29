# 🏠 homelab-notes

### Linux · Proxmox VE · Docker · Monitoring · Networking · Troubleshooting

Hands-on infrastructure lab used to practice Linux administration, virtualization,
containers, monitoring, networking and systematic troubleshooting.

> **Status:** the original two-node lab ran from 2025 to 2026.  
> The hardware has since been repurposed, but the setup, projects and troubleshooting
> work remain documented here.

🌐 [Portfolio](https://gt0u-labs.github.io/) ·
🔐 [Security learning log](https://github.com/gt0u-labs/security-learning-log)

---

## 🧭 Lab Overview

The lab consisted of two physical nodes managed remotely through SSH and the
Proxmox web interface.

### Node 1 — Ubuntu Server

**Role:** applications, logging and monitoring

- Ubuntu Server
- Headless administration over SSH
- Docker
- Docker Compose
- Grafana
- Loki
- Promtail
- Uptime Kuma
- Nginx

Used for containerized services, centralized logging, monitoring and
infrastructure experiments.

### Node 2 — Proxmox VE

**Role:** virtualization and security lab

- Proxmox VE bare-metal hypervisor
- VM provisioning
- LVM storage
- Virtual networking
- PCI / GPU passthrough
- USB passthrough

Virtual machines included:

**Kali Linux**
- Network reconnaissance
- Security practice
- Nmap
- GPU passthrough to a physical monitor

**Ubuntu Server**
- Infrastructure testing
- Docker
- Local LLM inference with Ollama + Open WebUI

---

## 🔧 Selected Projects

### Service Monitoring & Recovery

A small Docker Compose environment using Nginx and Uptime Kuma.

The Nginx service was stopped intentionally to simulate an outage.
Uptime Kuma detected the failure, the service was restored and recovery was
verified through monitoring and direct HTTP checks.

→ [View project](projects/service-monitoring-incident)

---

### Docker Compose — Nginx

Practical Docker Compose exercises covering:

- Container definitions
- Port mapping
- Service lifecycle
- Docker networking
- Nginx deployment

→ [View project](projects/docker-compose-nginx)

---

### First Nginx Container

Early Docker exercise used to understand the basic container workflow before the
lab moved onto more complex Compose-based infrastructure.

→ [View project](projects/docker-nginx-first-service)

---

## 🧰 Support Playbook

A small first-response troubleshooting runbook built from problems encountered
while running the lab.

Current scenarios include:

- Service outages
- SSH connectivity problems
- Disk space issues
- Memory/resource problems
- Docker storage usage
- Log-driven troubleshooting

The basic approach is:

```text
observe symptoms
      ↓
collect evidence
      ↓
identify the failing layer
      ↓
apply the smallest safe fix
      ↓
verify recovery
      ↓
document the result
