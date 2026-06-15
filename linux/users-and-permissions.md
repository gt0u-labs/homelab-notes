# Linux Users and Permissions

## Objective

Document basic Linux user and permission concepts.

This note focuses on simple commands I have used while working with Linux files and scripts.

## Basic Concepts

Linux files have permissions that control who can:

- read a file
- write/edit a file
- execute a file

The main permission letters are:

```text
r = read
w = write
x = execute
```

## Useful Commands

### Check current user

```bash
whoami
```

Shows the current Linux user.

### Check user ID and groups

```bash
id
```

Shows the current user's UID, GID and groups.

### List files with permissions

```bash
ls -l
```

Shows files with permissions, owner and group.

Example output:

```text
-rw-r--r-- 1 user user 120 file.txt
-rwxr-xr-x 1 user user 200 script.sh
```

## Making a Script Executable

I have used this command to make scripts executable:

```bash
chmod +x script.sh
```

After that, the script can be executed with:

```bash
./script.sh
```

## Numeric Permissions

Linux can also use numeric permissions such as:

```text
644
755
777
```

I am documenting these as part of my learning process.

Basic idea:

```text
4 = read
2 = write
1 = execute
```

Examples:

```text
644 = owner can read/write, others can read
755 = owner can read/write/execute, others can read/execute
777 = everyone can read/write/execute
```

## Important Note

`chmod 777` should usually be avoided because it gives everyone full permissions.

It may fix a problem temporarily, but it is not a safe default.

## What I Learned

I already knew how to use `chmod +x` to make scripts executable.

Now I am learning how Linux numeric permissions work and why permissions like `644`, `755` and `777` are different.