# 🏠 homelab-notes

Personal infrastructure, Linux, virtualization and self-hosting experiments — documented while building practical systems administration, networking and security skills.

🌐 Full portfolio: [gt0u-labs.github.io](https://gt0u-labs.github.io)

## 📚 Topics

* Proxmox VE virtualization
* GPU passthrough & local LLM inference (Ollama, Open WebUI)
* Ubuntu Server administration
* Docker & Docker Compose
* Centralized log monitoring (Grafana, Loki, Promtail)
* Network reconnaissance (Nmap, Kali Linux)
* SSH remote management
* Reverse proxies & tunneling (Tailscale)
* Incident simulation & recovery

---

## 🛠️ Current Lab Setup

**Node 1 — Application & Monitoring Server**
* Ubuntu Server (headless, SSH-managed)
* Docker & Docker Compose
* Grafana + Loki + Promtail — centralized log monitoring stack
* Uptime Kuma — service availability monitoring

**Node 2 — Virtualization Host**
* Proxmox VE (bare-metal hypervisor)
* Ubuntu Server VM — general-purpose target/test environment
* Kali Linux VM — network reconnaissance and security practice
* GPU passthrough configured to a dedicated VM for local LLM inference (Ollama + Open WebUI via Docker) — diagnosed and resolved a PCIe device-visibility issue at the host BIOS/IOMMU level

Both nodes are managed remotely over SSH and the Proxmox web interface — no physical keyboard/monitor required for day-to-day operation.

---

## 📖 Notes & Documentation

This repository contains practical notes, configurations and learning logs from hands-on infrastructure work. The goal is to progressively build real-world skills in:

* Linux system administration
* Virtualization and VM lifecycle management
* GPU passthrough and hardware-level virtualization troubleshooting
* Container workflows
* Centralized logging and observability
* Basic network security practices
* Remote infrastructure management

---

## 🚀 Current Focus

Currently learning and practicing:

* Proxmox VE administration (storage, networking, VM provisioning)
* Log analysis and dashboard building in Grafana
* Nmap-based network reconnaissance in a controlled lab
* Running and comparing local LLMs (Hermes3, Qwen2.5) for agent tooling
* CompTIA Network+ fundamentals

---

## ⚡ Philosophy

Learning by building.

Every project here is a hands-on experiment — set up, broken on purpose, fixed, and documented — focused on understanding how real systems behave outside of tutorials.
