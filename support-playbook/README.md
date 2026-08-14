# Support Playbook

A small collection of first-response steps I follow when something breaks in the lab, written the way I'd want a runbook to read in a real support environment — short, checklist-first, no guessing.

## Service is down

1. `systemctl status <service>` — is it running at all?
2. `journalctl -u <service> --since "30 min ago"` — what does it say right before it stopped?
3. Check the monitoring dashboard (Grafana / Uptime Kuma) — is this isolated or part of a wider issue?
4. Restart only if the logs point to something safe to restart — see [services-and-logs.md](../linux/services-and-logs.md).
5. Confirm recovery in the dashboard, then write a short incident note (see [service-monitoring-incident](../projects/service-monitoring-incident) for a full example).

## Can't reach a host over SSH

1. `ping <host>` — is it a network problem or an SSH problem?
2. Check the host is actually powered on / VM is running (Proxmox web console).
3. `ssh -v user@host` — verbose mode usually shows exactly where the connection fails.
4. Check firewall/port forwarding if it's a fresh VM.

## Disk or resource issues

1. `df -h` — out of disk space?
2. `free -h` — out of memory?
3. `docker system df` — Docker images/volumes eating disk space?
4. Clean up safely (`docker system prune`) only after checking what would be removed.

---

This is a working document — it grows as I run into new problems and document how I solved them.
