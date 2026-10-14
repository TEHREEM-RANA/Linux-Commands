# 15-01 Command Cheat Sheet

## Look around, create, copy, view

| Group | Commands |
|---|---|
| Look around | `pwd`, `ls` (`-l -a -h`), `cd` |
| Create | `mkdir`, `mkdir -p`, `touch`, `echo "text" > file` |
| Copy / move / delete | `cp` (`-r`), `mv`, `rm` (`-r`, `-f`) |
| View | `cat`, `less`, `head -n`, `tail -n`, `tail -f` |
| Search / link | `find . -name "*.txt"`, `ln -s` |
| Pipes | `cmd1 \| cmd2`, `grep word` |

## Permissions and ownership

| Group | Commands |
|---|---|
| See | `ls -l`, `ls -ld dir` |
| Change permissions | `chmod 644 file`, `chmod 755 script.sh`, `chmod u+x script.sh` |
| Ownership | `chown user file`, `chown user:group file`, `chgrp group file` |
| Default mask | `umask`, `umask -S`, `umask 027` |

## Users and system

| Group | Commands |
|---|---|
| Users | `whoami`, `who`, `id`, `groups`, `adduser`, `usermod -aG`, `userdel -r`, `passwd`, `su -` |
| Terminal and date | `tty`, `date`, `date "+%Y-%m-%d"`, `cal` |
| System | `uname -a`, `cat /etc/os-release`, `hostnamectl`, `nproc`, `ps`, `top`, `free -h`, `df -h`, `lsblk`, `du -sh` |

## Software, services, processes

| Group | Commands |
|---|---|
| Packages | `apt update`, `apt upgrade`, `apt install`, `apt remove`, `apt purge`, `apt search`, `apt show` |
| Processes | `ps aux`, `pgrep -a`, `top`, `htop`, `kill`, `kill -9`, `pkill` |
| Services | `systemctl status/start/stop/restart/reload/enable/disable`, `journalctl -u name -n 50` |

## Files, schedule, network

| Group | Commands |
|---|---|
| Archives | `tar -cf`, `tar -tf`, `tar -xf`, `tar -czf`, `tar -xzf`, `gzip`, `gunzip`, `zip -r`, `unzip` |
| Environment | `echo $PATH`, `export`, `printenv`, `which`, `command -v`, `type`, `source ~/.bashrc` |
| Cron | `crontab -l`, `crontab -e` |
| Transfer | `ssh`, `scp`, `sftp`, `rsync -av` |
| Web | `curl http://127.0.0.1`, `nginx -t`, `ss -tlnp` |

## Permission numbers

`r = 4`, `w = 2`, `x = 1`. `u` = owner, `g` = group, `o` = others, `a` = all.

| Mode | Use |
|---|---|
| 755 | Scripts, shared folders |
| 644 | Shared files |
| 700 | Private folders |
| 600 | Private files |

Rules to remember:

- File `x` = run it. Directory `x` = enter it. Directory `r` = list it. Directory `w` = create or delete items.
- Permission, owner, group and umask are four independent controls.
- `chmod 777` is risky. Do not reach for `sudo` first when you see "permission denied".

## Shell scripting

| Topic | Syntax |
|---|---|
| Variable | `name="Tehreem"`, use `"$name"` |
| Input | `read -p "Name: " name`, `$1 $2 $# $@` |
| Output | `echo "text"`, `printf "%s\n" "$x"`, `>`, `>>` |
| Arithmetic | `$((a + b))`, `bc` for decimals |
| Condition | `if [ $a -gt 5 ]; then ... elif ... else ... fi` |
| Case | `case "$x" in a) ... ;; *) ... ;; esac` |
| Loops | `for i in 1 2 3`, `while [ ... ]`, `until [ ... ]`, `break`, `continue` |
| Array | `arr=(a b c)`, `${arr[1]}`, `${arr[@]}`, `${#arr[@]}` |
| Associative array | `declare -A m; m[key]=value; ${!m[@]}` |
| Function | `name() { ...; }`, `local`, `return` |
| Exit status | `$?`, `exit 0`, `&&`, `\|\|` |

Reminders: no spaces around `=`, always quote `"$var"`, `$(( ))` uses integers only.

