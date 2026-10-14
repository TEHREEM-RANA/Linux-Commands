# 02-02 CPU, Memory, Disk Information

The kernel manages CPU, RAM and storage. Each one has a command.

## CPU

```bash
nproc
```
What it does: prints the number of usable processors/cores. Example: `4`

```bash
lscpu
```
What it does: summary of CPU type, cores and model.

```bash
cat /proc/cpuinfo
```
What it does: raw list for each core.

## Memory (RAM)

```bash
free -h
```
What it does: readable summary: total, used, available.

```bash
cat /proc/meminfo
```
What it does: detailed memory information from the kernel.

```bash
vmstat
```
What it does: snapshot of memory, swap and the run queue.

## Storage (disk)

```bash
df -h
```
What it does: shows mounted filesystems and free space.

```bash
lsblk
```
What it does: lists disks and partitions.

```bash
du -sh /home
```
What it does: shows how much space one folder uses. Change `/home` to any path.

## Live view

```bash
top
```
Press `q` to quit.

```bash
htop
```
A friendlier version. Install first if needed: `sudo apt install htop`

## About /proc

`/proc` is not a normal folder on disk. It is a window the kernel gives you to read live system state. `cat /proc/meminfo` asks the kernel a question.


Next: `../03-users-and-groups/01-users.md`
