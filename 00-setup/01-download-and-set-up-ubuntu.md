# 00-01 Download and Set Up Ubuntu

This repository uses **Ubuntu LTS** everywhere. LTS means Long Term Support: the version gets updates for years. The version number changes (22.04, 24.04, 26.04, ...), so always pick the newest **LTS**.

You can get an Ubuntu terminal in three ways. Choose **one**.

| Way | Gives you | Best for |
|---|---|---|
| WSL (Windows only) | Ubuntu terminal inside Windows | Quick start, only commands needed |
| VirtualBox (Windows or Mac) | Full Ubuntu desktop inside your PC | Learning like a real computer |
| VPS (rented online server) | A real Ubuntu server on the internet | Server practice, Nginx, cron, SSH |

---

## Way 1: Ubuntu with WSL (Windows)

WSL = Windows Subsystem for Linux. No VirtualBox needed.

1. Right-click Start → open **PowerShell as Administrator**.
2. Run:

```powershell
wsl --install -d Ubuntu
```
What it does: installs WSL and Ubuntu.

```powershell
wsl --install
```
What it does: installs WSL with the default distro (it is Ubuntu).

```powershell
wsl --list --online
```
What it does: shows the distro names you can install with `-d`.

3. Restart the PC if Windows asks.
4. Open **Ubuntu** from the Start menu.
5. Create a UNIX username (for example `tehreem`) and a password. This is **not** your Windows password. When you type the password, nothing appears on screen. This is normal.

Check that it works:

```bash
uname -a
cat /etc/os-release
ls -la
```

Useful WSL commands (run in PowerShell, not in Ubuntu):

| Command | What it does |
|---|---|
| `wsl --list --verbose` | Shows installed distros and their state |
| `wsl -d Ubuntu` | Opens Ubuntu |
| `wsl --shutdown` | Stops all WSL distros |

Your Windows files are inside Ubuntu at `/mnt/c`.
WSL is not a public server. It is not reachable from the internet unless you set that up yourself.

---

## Way 2: Ubuntu with VirtualBox

Virtualization = a second computer inside your laptop. Your laptop is the **host**. Ubuntu inside VirtualBox is the **guest**. They stay separate.
Use this only if your PC has spare RAM and CPU. Give the VM as much RAM and CPU as you can spare.

### Step 1: Install VirtualBox

1. Search "download VirtualBox" and open the **official** site.
2. Download the version for your system (Windows hosts or macOS).
3. Run the installer: Next → accept the license → Install → Finish.

### Step 2: Download Ubuntu

1. Search "download Ubuntu LTS" and open the **official Ubuntu** site.
2. Download the newest **LTS** ISO file.
3. Match your CPU:
   - Intel or AMD (almost every Windows PC and Intel Mac): **AMD64 / x86-64** ISO
   - Apple Silicon Mac (M1, M2, ...): **ARM64** ISO

Download the ISO only once.

### Step 3: Create the VM

1. VirtualBox → **New** → Type: Linux → Version: Ubuntu.
2. Select the Ubuntu ISO.
3. Set a simple username and password that you can remember.
4. Give RAM and CPU as much as you can spare.
5. Disk: 100 GB if your PC can take it. Reduce it if the PC is already slow.
6. Finish, then **Start** the VM. The first boot is often slow. Wait.
7. Log in with the user you created.

### Step 4: Open the terminal inside Ubuntu

```text
Ctrl + Alt + T
```
Or: Activities → type `terminal` → Enter. Or: right-click on the desktop → Open in Terminal.

Check it:

```bash
uname -a
cat /etc/os-release
uname -m
ls -la
```

| Command | What it does |
|---|---|
| `uname -m` | Shows CPU type: `x86_64` (Intel/AMD) or `aarch64` (Apple Silicon) |
| `ls -la` | Shows all files, including hidden ones |

If the VM does not boot, the ISO type is usually wrong for your CPU.

Use the terminal **inside the VM**. The Windows terminal or the Mac Terminal talks to Windows or macOS, not to Ubuntu.

---

## Way 3: Ubuntu on a VPS (online server)

A VPS (Virtual Private Server) is an Ubuntu machine you rent in the cloud. You reach it over SSH. Commands you type run on that machine, not on your laptop. Closing your laptop does not stop the server.

### Step 1: Buy the plan

1. Choose a plan. Example: KVM 2 (2 CPU, 8 GB RAM, 100 GB disk). KVM 1 also works for light practice.
2. Choose **Ubuntu LTS** as the operating system. Linux has no OS license fee.
3. Pay. Skip add-ons you do not need.
4. Set a **root password** and write it down. Resetting it is possible, but forgetting it is painful.
5. Wait a few minutes for the setup to finish.

### Step 2: Connect with SSH

The panel gives you the server IP. Open your terminal (PowerShell, macOS Terminal, or Linux terminal) and run:

```bash
ssh root@203.0.113.10
```
What it does: connects to the VPS. Use **your** real IP.

```bash
ssh -p 22 root@203.0.113.10
```
What it does: same, but sets port 22 clearly.

```bash
ssh -i ~/.ssh/id_rsa root@203.0.113.10
```
What it does: connects with a key file instead of a password.

First time, it asks whether to trust the host. Type `yes`. Then paste the root password. Nothing is shown while you type it.

You should see `Welcome to Ubuntu` and a prompt like `root@srv...`. That prompt is the VPS.

```bash
hostname
uname -a
cat /etc/os-release
```

### If something breaks

On the VPS panel you can reset the root password, copy the SSH command again, or open the browser terminal. The browser terminal is the same machine as `ssh`.

---

Next: `02-confirm-you-are-on-ubuntu.md`
