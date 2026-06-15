# Linux Services and Logs

## Objective

Document basic commands used to inspect Linux services and logs during troubleshooting.

Services and logs are important because many server problems are related to failed processes, crashed services or configuration errors.

## Basic Concepts

A Linux service is a background process managed by the system.

Examples:

- SSH server
- web server
- database service
- Docker service

Logs are records of what happened on the system or inside a service.

## Useful Commands

### Check systemd version

```bash
systemctl --version
```

### List running services

```bash
systemctl list-units --type=service --state=running
```

### Check the status of a service

```bash
systemctl status service-name
```

Example:

```bash
systemctl status ssh
```

### Start a service

```bash
sudo systemctl start service-name
```

### Stop a service

```bash
sudo systemctl stop service-name
```

### Restart a service

```bash
sudo systemctl restart service-name
```

### Enable a service on boot

```bash
sudo systemctl enable service-name
```

### View recent system logs

```bash
journalctl -xe
```

### View logs for a specific service

```bash
journalctl -u service-name
```

Example:

```bash
journalctl -u ssh
```

### View logs from the last hour

```bash
journalctl --since "1 hour ago"
```

## Basic Troubleshooting Flow

When a service is not working:

1. Check if the service exists.
2. Check if the service is running.
3. Check service status.
4. Read the logs.
5. Look for errors.
6. Do not restart production services without permission.

## Example Investigation

If SSH is not working, I would check:

```bash
systemctl status ssh
journalctl -u ssh --since "1 hour ago"
```

Then I would look for:

- failed login attempts
- configuration errors
- service not running
- port or firewall issues

## Important Note

Before restarting a service, always understand the possible impact.

Restarting a service may disconnect users or interrupt active processes.

## What I Learned

Services and logs are one of the first places to check when troubleshooting Linux systems.

A good troubleshooting process starts by checking status, reading logs and understanding the impact before making changes.