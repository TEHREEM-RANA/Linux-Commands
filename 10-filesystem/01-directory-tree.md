# 10-01 The Linux Directory Tree

Everything starts at `/`.

```text
/
├── home/   → users' personal files
├── etc/    → system configuration
├── var/    → changing data, logs, caches
├── usr/    → programs and shared resources
├── bin/    → essential commands
├── tmp/    → temporary files
└── root/   → the root user's home
```

Seven to remember: `/` everything · `/home` users · `/etc` configuration · `/var` changing data/logs · `/usr` programs · `/bin` essential commands · `/tmp` temporary files.

## Walk the tree

```bash
cd /
ls
```

## The important folders with commands

| Folder | Meaning | Command to try |
|---|---|---|
| `/home` | Users' files (`/home/tehreem` = `~`) | `ls /home` |
| `/etc` | Configuration | `cat /etc/hosts` |
| `/etc/passwd` | Info about users | `cat /etc/passwd` |
| `/var` | Data that changes (logs, cache) | `ls /var/log` |
| `/usr` | Installed programs | `ls /usr/bin` |
| `/bin` | Essential commands (often a link to `/usr/bin`) | `ls -ld /bin` |
| `/tmp` | Temporary files (may be deleted on reboot) | `cd /tmp` |

```bash
which python3
```
What it does: shows where a program lives. Example: `/usr/bin/python3`

```bash
ls -ld /bin
```
What it does: on modern Linux you may see `/bin -> usr/bin` (a symbolic link).

Logs: if a server has a problem, look in `/var/log` first (`/var/log/syslog`, `/var/log/auth.log`).

## Other folders

| Directory | Purpose |
|---|---|
| `/boot` | Files needed to boot Linux |
| `/dev` | Devices shown as files |
| `/proc` | Information about processes and the kernel |
| `/sys` | Kernel and device information |
| `/run` | Runtime data since boot |
| `/mnt` | Manual mount points |
| `/media` | Removable media |
| `/opt` | Optional / third-party software |
| `/sbin` | System administration commands |

## `/` vs `/root` vs `~`

- `/` = top of the tree
- `/root` = home of the root user
- `~` = your own home folder


Next: `../11-nginx/01-nginx.md`
