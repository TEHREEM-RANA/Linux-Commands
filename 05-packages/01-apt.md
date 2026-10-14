# 05-01 Package Management with apt (Ubuntu / Debian)

`apt` installs, updates and removes software. Packages come from **repositories** (online software stores).

## The two most confused commands

```bash
sudo apt update
```
What it does: downloads the **list** of available packages and versions. It does **not** update your software.

```bash
sudo apt upgrade
```
What it does: installs the available updates for packages you already have.

```bash
sudo apt update && sudo apt upgrade
```
What it does: runs both. `&&` means the second runs only if the first succeeds.

Phone analogy: `update` = check which apps have updates. `upgrade` = install them.

```bash
sudo apt full-upgrade
```
What it does: like `upgrade`, but it may also install or remove packages to finish the job. More aggressive.

## Install, remove, search

| Command | What it does |
|---|---|
| `sudo apt install nginx` | Install a package |
| `sudo apt install git curl wget` | Install several packages |
| `sudo apt remove nginx` | Remove the software, keep its config files |
| `sudo apt purge nginx` | Remove the software **and** its config files |
| `apt search nginx` | Search by name or description |
| `apt show nginx` | Show version, dependencies, description, size |
| `apt list --installed` | List installed packages |
| `apt list --installed \| grep nginx` | Check if one package is installed |
| `apt policy nginx` | Show installed and available versions |
| `sudo apt autoremove` | Remove packages no longer needed |
| `sudo apt clean` | Delete downloaded package files from the cache |

`remove` = remove software. `purge` = remove software + configuration.

## Repositories

APT reads its sources from:

```text
/etc/apt/sources.list
/etc/apt/sources.list.d/
```

Flow: Repository → package lists (`apt update`) → `apt install` → package downloaded → installed.

## apt vs apt-get

`apt` is the modern, friendly command. `apt-get` is older and still used in scripts. This repository uses `apt`.

## What can go wrong

An upgrade can bring a new bug, a config change, or a service that fails to restart. On a production server, take a backup or snapshot before big upgrades.


Next: `../06-processes-and-services/01-processes.md`
