# 00-02 Confirm You Are on Ubuntu

Three questions to ask on any new machine: **Which kernel? Which Ubuntu version? Which user?**
Run these commands once after you set up Ubuntu.

## Kernel

```bash
uname -s
```
What it does: prints the kernel name. Output: `Linux`

```bash
uname -a
```
What it does: prints everything in one line: hostname, kernel version, CPU type.

```bash
uname -r
```
What it does: prints only the kernel release number (used in docs and bug reports).

```bash
uname -v
```
What it does: prints the kernel build information.

```bash
uname -m
```
What it does: prints the CPU type (`x86_64` or `aarch64`).

```bash
cat /proc/version
```
What it does: asks the kernel for its version. It also shows the compiler used to build it.

## Ubuntu version

```bash
cat /etc/os-release
```
What it does: shows the name and version of your Ubuntu. This is the most reliable way.

```bash
hostnamectl
```
What it does: shows the OS name and the kernel together.

```bash
cat /etc/issue
```
What it does: shows the short login banner. Less complete.

```bash
lsb_release -a
```
What it does: shows the same idea in an older format. If it says command not found, install it with `sudo apt install lsb-release`.

If `uname -s` says `Linux` and `/etc/os-release` says `Ubuntu`, then the kernel is Linux and the operating system (distribution) is Ubuntu.

## Who, where, which machine

```bash
whoami
```
What it does: prints your username. Example: `tehreem`

```bash
pwd
```
What it does: prints your current folder. Example: `/home/tehreem`

```bash
hostname
```
What it does: prints the machine name.

## First update of a fresh Ubuntu

```bash
sudo apt update
sudo apt upgrade
```
What it does: `update` refreshes the list of available software. `upgrade` installs the new versions. More in `../05-packages/01-apt.md`.

## Two habits from day one

- Linux commands are **case sensitive**. `Uname` is wrong. `uname` is right.
- Try the extra options (`-a`, `-r`, ...), not only the first command.

Next: `../01-basics/01-navigation.md`
