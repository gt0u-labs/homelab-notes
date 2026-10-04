# 🏠 homelab-notes

### Linux · Proxmox VE · Docker · Monitoring · Networking · Troubleshooting

Hands-on infrastructure lab used to practice Linux administration, virtualization,
containers, monitoring, networking and systematic troubleshooting.

> **Status:** the original two-node lab ran from 2025 to 2026.  
> The hardware has since been repurposed, but the setup, projects, incident tests
> and troubleshooting work remain documented here.

🌐 [Portfolio](https://gt0u-labs.github.io/) ·
🔐 [Security learning log](https://github.com/gt0u-labs/security-learning-log)

---

## 🧭 Lab Overview

The lab consisted of two physical nodes managed remotely through SSH and the
Proxmox web interface.

```text
                    Admin workstation
                          │
                 SSH / Web interfaces
                          │
             ┌────────────┴────────────┐
             │                         │
     Node 1 — Ubuntu Server     Node 2 — Proxmox VE
             │                         │
      Docker / Compose             Virtual machines
             │                         │
   Grafana · Loki · Promtail     ┌─────┴─────┐
        Uptime Kuma              │           │
           Nginx               Kali      Ubuntu Server
                                │           │
                          GPU passthrough  Ollama /
                                         Open WebUI
```

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

Used for containerized services, centralized logging, service monitoring and
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

A Docker Compose environment using Nginx and Uptime Kuma to practice a simple
service outage and recovery workflow.

The Nginx container was stopped intentionally to simulate an outage.

Uptime Kuma detected the failure, the service was restored and recovery was
verified through both monitoring and direct HTTP checks.

The project includes screenshots showing the service in:

`UP` → `DOWN` → `RECOVERED`

→ [View project](projects/service-monitoring-incident)  
→ [Read the incident report](projects/service-monitoring-incident/incident-report.md)

---

### Docker Compose — Nginx

A small Docker Compose lab focused on defining and managing a repeatable
containerized service.

Covered:

- Container definitions
- Port mapping
- Service lifecycle
- Docker networking
- Log inspection
- HTTP verification
- Stop/start recovery testing

→ [View project](projects/docker-compose-nginx)

---

### First Nginx Container

An earlier Docker lab documenting a basic Nginx deployment through WSL and
Docker Desktop.

Docker commands were initially unavailable inside the Ubuntu WSL distribution
because Docker Desktop WSL integration had not been enabled.

The issue was identified, corrected and verified before continuing with the
container test.

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

The general approach is:

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
```

The goal is to avoid changing things blindly and instead work from observable
symptoms, logs and system state.

→ [View the support playbook](support-playbook)

---

## 🐧 Linux Notes

Practical notes created while working with Linux systems.

### Basic System Checks

A first-response checklist covering:

- Current user and working directory
- Files and permissions
- Disk usage
- Memory usage
- Running processes
- Network interfaces
- Routing
- Basic connectivity

→ [Linux basic system checks](linux/linux-basic-system-checks.md)

### Services & Logs

Notes on:

- `systemctl`
- Service state
- Start / stop / restart
- Service enablement
- `journalctl`
- Log-driven troubleshooting

→ [Linux services and logs](linux/services-and-logs.md)

### Users & Permissions

Notes covering:

- Users and groups
- Ownership
- Read / write / execute permissions
- Numeric modes such as `644` and `755`
- Why `chmod 777` should not be used as a default fix

→ [Linux users and permissions](linux/users-and-permissions.md)

---

## 🎮 GPU Passthrough — Proxmox / VFIO

One of the more involved troubleshooting exercises in the lab.

The goal was to run a Kali Linux VM on a physical monitor using an MSI GTX 1080
Gaming X passed directly through from the Proxmox host.

Initial video output failed with:

```text
vfio-pci 0000:01:00.0:
Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
```

`dmesg` helped narrow the problem down to the GPU ROM.

The setup was eventually fixed using a card-specific VBIOS through `romfile=`.

Further troubleshooting included:

- USB keyboard and mouse passthrough
- VM boot-order correction
- Virtual display configuration
- PCI / VFIO troubleshooting
- Recovery after an unnecessary guest GPU-driver installation broke the VM

The last mistake forced a rebuild and became part of the documentation rather
than being hidden.

→ [Read the full VFIO troubleshooting write-up](https://github.com/gt0u-labs/security-learning-log/blob/main/writeups/proxmox-gpu-passthrough.md)

---

## 📊 Monitoring & Logging

The Ubuntu Server node ran a self-hosted monitoring environment using:

**Grafana · Loki · Promtail · Uptime Kuma**

The setup was used to practice:

- Centralized log collection
- Searching service logs
- Monitoring containerized services
- Basic dashboard creation
- Availability monitoring
- Diagnosing failures from logs

Uptime Kuma was also used separately for service availability checks and the
documented Nginx outage/recovery exercise.

> Additional Grafana, Loki and Promtail configuration notes are still being
> organized for this repository.

---

## 🌐 Networking

Networking work across the lab included:

- SSH
- DNS
- NAT and port forwarding
- Docker networking
- Nginx
- Reverse proxies
- Tailscale
- VM networking
- Nmap reconnaissance

Security and reconnaissance exercises were performed only against systems and
networks inside my own controlled lab environment.

---

## 📁 Repository Structure

```text
homelab-notes/
│
├── docker/
│   └── README.md
│
├── linux/
│   ├── linux-basic-system-checks.md
│   ├── services-and-logs.md
│   └── users-and-permissions.md
│
├── networking/
│   └── README.md
│
├── projects/
│   ├── docker-nginx-first-service/
│   ├── docker-compose-nginx/
│   └── service-monitoring-incident/
│       ├── README.md
│       ├── docker-compose.yml
│       ├── incident-report.md
│       └── screenshots/
│
└── support-playbook/
    └── README.md
```

---

## 🧪 What the Lab Was Used For

The goal was not simply to keep services running.

The environment was used to practice:

- Linux system administration
- VM lifecycle management
- Docker and Docker Compose
- Service monitoring
- Centralized logging
- Network reconnaissance
- Remote administration
- Infrastructure troubleshooting
- Failure recovery
- Technical documentation

When something failed, the approach was to work from system state, logs and
observable symptoms before changing configuration.

---

## 🚀 Current Direction

Building toward junior roles in:

- Technical Support
- Infrastructure Support
- NOC / Operations
- Junior System Administration
- Defensive Security / SOC

Current areas of study include enterprise networking, Windows Server,
Active Directory and defensive monitoring.

→ [Security training and labs](https://github.com/gt0u-labs/security-learning-log)

---

## ⚡ Approach

**Build it. Observe it. Break it. Understand why. Fix it. Document it.**

The value of the lab was not the number of services running.

It was learning how to approach a system when something stopped working.
