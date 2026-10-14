# 06-01 Processes

- **Program** = code stored on disk.
- **Process** = that program running now.
- Every process has a **PID** (process ID).

## ps — snapshot of processes

```bash
ps
```
What it does: shows processes of your current terminal.

```text
  PID TTY          TIME CMD
 1234 pts/0    00:00:00 bash
 5678 pts/0    00:00:00 ps
```

```bash
ps -e
```
What it does: shows all processes.

```bash
ps aux
```
What it does: shows all users' processes with details.

| Column | Meaning |
|---|---|
| USER | Who owns the process |
| PID | Process ID |
| %CPU | CPU usage |
| %MEM | Memory usage |
| STAT | Process state |
| START | When it started |
| TIME | CPU time used |
| COMMAND | The program |

## Find one process

```bash
ps aux | grep nginx
```
What it does: lists all processes, then keeps lines with `nginx`.

```bash
pgrep nginx
pgrep -a nginx
```
What it does: prints PIDs. `-a` also prints the full command line.

## Live view

```bash
top
```
What it does: live updating list. Look at `%CPU` and `%MEM` when the server is slow. Press `q` to quit.

```bash
htop
```
What it does: interactive viewer (scroll, sort, search, kill). Install: `sudo apt install htop`

| Tool | Use |
|---|---|
| `ps` | Snapshot |
| `top` | Live monitoring |
| `htop` | Interactive live monitoring |

## Stop a process

```bash
kill 1234
```
What it does: sends SIGTERM = "please shut down". The program can clean up first.

```bash
kill -9 1234
```
What it does: sends SIGKILL = "stop now". The program cannot catch it. Use it only when normal `kill` fails.

```bash
pkill nginx
```
What it does: sends a termination signal to all processes with that name. Be careful: a wrong name can stop more than you wanted.


Next: `02-services-systemctl.md`
