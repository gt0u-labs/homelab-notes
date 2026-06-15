# Linux Users and Permissions

## Goal

Document basic Linux user and permission commands.

I already used `chmod +x` before to make scripts executable, but I wanted to understand numeric permissions like `644`, `755` and `777` better.

## Environment

* WSL Ubuntu
* Windows Terminal
* VS Code

## Commands Used

```bash
whoami
id
ls -l
chmod +x script.sh
chmod 644 file.txt
chmod 755 script.sh
```

## Notes

Linux permissions control who can read, write or execute a file.

```text
r = read
w = write
x = execute
```

They apply to:

```text
owner / group / others
```

The numeric values are:

```text
4 = read
2 = write
1 = execute
```

Examples:

```text
644 = owner can read/write, group and others can read
755 = owner can read/write/execute, group and others can read/execute
777 = everyone can read/write/execute
```

## What I Already Knew

I already knew how to use:

```bash
chmod +x script.sh
```

This makes a script executable so it can be run with:

```bash
./script.sh
```

## Important Note

`chmod 777` should not be used as a normal fix.

It can make permission problems disappear, but it gives too much access and is not safe by default.

## What I Learned

I understood the basic logic behind numeric permissions.

I still need to practice this more with real files and folders, but now `644`, `755` and `777` make more sense than before.
