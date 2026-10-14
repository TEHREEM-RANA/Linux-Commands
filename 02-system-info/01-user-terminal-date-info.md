# 02-01 Who Am I? Terminal, Date, OS Info

These commands let you "see" the OS working from the shell.

| Command | What it does | Example output |
|---|---|---|
| `whoami` | Shows the username your shell is using | `tehreem` |
| `who` | Shows all users logged in | `tehreem pts/0 2026-09-22 10:15` |
| `who -H` | Same as `who` with column headers | |
| `tty` | Shows the terminal device linked to your input | `/dev/pts/0` |
| `id` | Shows your user ID and group IDs | `uid=1000(tehreem) gid=1000(tehreem) ...` |
| `date` | Shows system date and time | |
| `cal` | Shows a calendar | |
| `uname -a` | Shows kernel name, version, CPU type | |
| `cat /etc/os-release` | Shows which distribution you use | |

## who vs whoami

- `who` = everybody logged in.
- `whoami` = which account **your** shell is using.

## tty breakdown

`/dev/pts/0`

- `/dev` = device folder
- `pts` = pseudo-terminal
- `0` = this terminal's number

The output is different for a physical terminal, an SSH session, or a cloud shell. You do not need to memorise every form.

## date formats

```bash
date
date "+%Y-%m-%d"
date "+%H:%M:%S"
```

| Symbol | Meaning |
|---|---|
| `%Y` | Year |
| `%m` | Month |
| `%d` | Day |
| `%H` | Hour |
| `%M` | Minute |
| `%S` | Second |

Save a date in a variable (used in scripts):

```bash
today=$(date +%F)
echo $today
```

## cal

```bash
cal
cal 2026
cal 9 2026
```
What it does: current month / whole year / September 2026.

`cal` may not be installed on some distributions. If missing, install `ncal` or `util-linux` with your package manager. Do not assume every system has it.

## Running processes (quick look)

```bash
ps
ps -e
top
```
- `ps` = your processes
- `ps -e` = all processes
- `top` = live view of CPU and RAM. Press `q` to quit.

## Use these commands to see OS types

| Command | What it shows |
|---|---|
| `who` (more than one user) | Multi-user system |
| `ps -e` (many processes) | Multitasking |
| `top` | Live CPU and RAM use |
| `uname -a` vs `cat /etc/os-release` | Kernel vs distribution |
| `nproc` | Number of CPU cores |


Next: `02-cpu-memory-disk-info.md`
