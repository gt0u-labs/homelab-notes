# Linux Basic System Checks

## Goal

Create a small checklist of basic Linux commands I can use when I first open a system and want to understand its current state.

This is not advanced, but it is useful as a first troubleshooting step.

## Environment

* Windows 11 Pro
* WSL Ubuntu
* Windows Terminal
* VS Code

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

## What I Checked

I used `whoami` and `pwd` to confirm the current user and working directory.

I used `ls -la` to list files with hidden files, permissions and ownership.

I used `df -h` and `free -h` to check disk and memory usage. I had not used `free -h` much before, so I added it to my basic checklist.

I used `ps aux` and `top` to check running processes.

I used `ip addr`, `ip route` and `ping` to check basic network information and connectivity.

## Result

The commands worked as expected in my WSL Ubuntu environment.

## What I Learned

This is a basic checklist, but it gives me a quick starting point before changing anything on a Linux system.

The main idea is:

```text
check first → understand the system → then troubleshoot
```
