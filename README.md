# 🏠 homelab-notes

Personal infrastructure, Linux, virtualization and self-hosting experiments — documented while building practical systems administration, networking and security skills.

> **Status:** this lab ran from 2025 to 2026. The hardware has since been repurposed — this repository documents the setup as it was built, including configuration, monitoring and troubleshooting.

🌐 Full portfolio: [gt0u-labs.github.io](https://gt0u-labs.github.io)

## 📚 Topics

* Proxmox VE virtualization
* GPU passthrough (VFIO) troubleshooting
* Local LLM inference (Ollama, Open WebUI)
* Ubuntu Server administration
* Docker & Docker Compose
* Centralized log monitoring (Grafana, Loki, Promtail)
* Network reconnaissance (Nmap, Kali Linux)
* SSH remote management
* Reverse proxies & tunneling (Tailscale)
* Incident simulation & recovery

---

## 🛠️ Lab Setup (2025–2026)

**Node 1 — Application & Monitoring Server**
* Ubuntu Server (headless, SSH-managed)
* Docker & Docker Compose
* Grafana + Loki + Promtail — centralized log monitoring stack
* Uptime Kuma — service availability monitoring

**Node 2 — Virtualization Host**
* Proxmox VE (bare-metal hypervisor)
* Ubuntu Server VM — test target and local LLM inference (Ollama + Open WebUI via Docker)
* Kali Linux VM — network reconnaissance and security practice, run on a physical monitor via GPU passthrough because the Proxmox web console was too laggy for GUI tools
* GPU passthrough troubleshooting — diagnosed a PCI ROM signature error through `dmesg` and resolved it with a card-specific VBIOS → [full write-up](https://github.com/gt0u-labs/security-learning-log/blob/main/writeups/proxmox-gpu-passthrough.md)

Both nodes were managed remotely over SSH and the Proxmox web interface.

---

## 📖 Notes & Documentation

This repository contains practical notes, configurations and learning logs from hands-on infrastructure work, covering:

* Linux system administration
* Virtualization and VM lifecycle management
* GPU passthrough and hardware-level virtualization troubleshooting
* Container workflows
* Centralized logging and observability
* Basic network security practices
* Remote infrastructure management

---

## 🧪 What the lab was used for

* Proxmox VE administration (storage, networking, VM provisioning)
* Log analysis and dashboard building in Grafana
* Nmap-based network reconnaissance in a controlled lab
* Running and comparing local LLMs (Hermes3, Qwen2.5) for agent tooling

## 🚀 Current Focus

* CompTIA Network+
* Defensive security training → [security-learning-log](https://github.com/gt0u-labs/security-learning-log)

---

## ⚡ Philosophy

Learning by building.

Every project here was a hands-on experiment — set up, broken on purpose, fixed, and documented — focused on understanding how real systems behave outside of tutorials.
