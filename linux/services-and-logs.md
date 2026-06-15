# Linux Services and Logs

## Goal

Document basic commands for checking Linux services and logs.

I already understood commands like `start`, `stop`, `restart` and `status`, but I had not used `journalctl` much before.

## Environment

* WSL Ubuntu
* Windows Terminal
* VS Code

## Commands Used

```bash
systemctl --version
systemctl list-units --type=service --state=running
systemctl status service-name
sudo systemctl start service-name
sudo systemctl stop service-name
sudo systemctl restart service-name
sudo systemctl enable service-name
journalctl -xe
journalctl -u service-name
journalctl -u service-name --since "1 hour ago"
```

## Service Commands

Basic meaning:

```text
start   = start the service now
stop    = stop the service now
restart = restart the service now
status  = check service status
enable  = make the service start automatically on boot
```

Example:

```bash
sudo systemctl start ssh
sudo systemctl enable ssh
```

`start` runs the service now.

`enable` makes it start automatically after reboot.

## Logs

`journalctl` is used to read system logs.

Useful examples:

```bash
journalctl -xe
journalctl -u ssh
journalctl -u ssh --since "1 hour ago"
```

## Basic Troubleshooting Flow

If a service is not working, I would check:

```text
1. Is the service installed?
2. Is it running?
3. What does systemctl status show?
4. What do the logs show?
5. Is it safe to restart it?
```

Example:

```bash
systemctl status ssh
journalctl -u ssh --since "1 hour ago"
```

## Important Note

In a real environment, restarting a service can affect users or running processes.

I should not restart production services without understanding the impact or asking first.

## What I Learned

The most useful new command for me here was `journalctl`.

Instead of guessing why something failed, I can check the service status and read logs first.
