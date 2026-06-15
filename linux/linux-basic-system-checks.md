# Linux Basic System Checks

## Objective

Document basic Linux commands used to inspect system status during troubleshooting.

This is a foundational troubleshooting checklist for Linux systems.

## Environment

- Windows 11 Pro
- WSL Ubuntu
- Windows Terminal
- VS Code

## Commands Used

```bash
whoami
pwd
ls -la
df -h
free -h
ps aux
top
ip addr
ip route
ping -c 4 google.com
```

## Command Notes

### `whoami`

Shows the current user.

```bash
whoami
```

### `pwd`

Shows the current working directory.

```bash
pwd
```

### `ls -la`

Lists files and directories, including hidden files, permissions and ownership.

```bash
ls -la
```

### `df -h`

Shows disk usage in a human-readable format.

```bash
df -h
```

### `free -h`

Shows memory usage in a human-readable format.

```bash
free -h
```

### `ps aux`

Lists running processes.

```bash
ps aux
```

### `top`

Shows live system resource usage.

```bash
top
```

### `ip addr`

Shows network interfaces and assigned IP addresses.

```bash
ip addr
```

### `ip route`

Shows the routing table.

```bash
ip route
```

### `ping`

Tests network connectivity.

```bash
ping -c 4 google.com
```

## Problems Encountered

No major issues during this first system check.

## What I Learned

Basic system checks are the first step before troubleshooting deeper Linux problems.

Before changing anything on a system, it is important to inspect:

- current user
- working directory
- disk usage
- memory usage
- running processes
- network interfaces
- routing
- basic internet connectivity