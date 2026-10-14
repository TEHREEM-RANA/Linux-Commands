# Linux Commands 

A step-by-step, command-based guide to Linux 
Every topic has its own file. Every command is shown with what it does,  with a short example.

Read it once from start to end and you will know how to use Linux: from installing Ubuntu, to files, users, permissions, software, services, web servers and shell scripting.

## What is inside

| Folder | What you learn |
|---|---|
| [`00-setup`](00-setup) | Download and set up Ubuntu (WSL, VirtualBox, VPS) and check it |
| [`01-basics`](01-basics) | `pwd`, `ls`, `cd`, `mkdir`, `touch`, `cp`, `mv`, `rm`, `cat`, `less`, `find`, pipes, `nano`, `sudo` |
| [`02-system-info`](02-system-info) | `whoami`, `who`, `tty`, `id`, `date`, `cal`, `uname`, `nproc`, `free`, `df`, `lsblk`, `du` |
| [`03-users-and-groups`](03-users-and-groups) | `adduser`, `su`, `usermod -aG`, `passwd`, `groupadd`, `userdel` |
| [`04-permissions`](04-permissions) | Reading `ls -l`, `chmod`, `chown`, `chgrp`, `umask`, fixing permission errors |
| [`05-packages`](05-packages) | `apt update`, `upgrade`, `install`, `remove`, `purge`, `search`, `show` |
| [`06-processes-and-services`](06-processes-and-services) | `ps`, `top`, `htop`, `kill`, `systemctl`, `journalctl` |
| [`07-environment`](07-environment) | Variables, `export`, `PATH`, `.bashrc`, `source` |
| [`08-archives`](08-archives) | `tar`, `gzip`, `gunzip`, `zip`, `unzip` |
| [`09-cron`](09-cron) | `crontab`, schedules, logs |
| [`10-filesystem`](10-filesystem) | The Linux folder tree: `/home`, `/etc`, `/var`, `/usr`, `/tmp` |
| [`11-nginx`](11-nginx) | Install Nginx, serve a page, test and reload |
| [`12-file-transfer`](12-file-transfer) | `ssh`, `scp`, `sftp`, `rsync`, FileZilla |
| [`13-shell-scripting`](13-shell-scripting) | Variables, input, output, arithmetic, conditions, loops, arrays, functions, exit status, comments |
| [`15-cheatsheets`](15-cheatsheets) | One-page command list and common errors |

## Shell scripting files

| File | Topic |
|---|---|
| `01-first-script.md` | Shebang, running a script |
| `02-variables.md` | Variables, types, quotes, scope |
| `03-input.md` | `read`, arguments `$1 $2`, reading files |
| `04-output.md` | `echo`, `printf`, redirection, pipes |
| `05-arithmetic.md` | `$(( ))`, `expr`, `let`, `bc` |
| `06-conditions.md` | `if`, `elif`, `else`, tests, `case` |
| `07-loops.md` | `for`, `while`, `until`, `select`, `break`, `continue` |
| `08-arrays.md` | Indexed and associative arrays |
| `09-functions.md` | Functions, `local`, `return` |
| `10-exit-status-and-comments.md` | `$?`, `exit`, comments |
| `11-example-menu-calculator.md` | A full menu calculator |

## How to read

1. Go through the folders in order.
2. Type each command in your Ubuntu terminal while you read.
3. Output can differ on your machine. This is normal.

## Be careful

- `rm` has no recycle bin. Deleted means gone.
- `chmod 777` removes almost all protection. Avoid it.
- Do not use `sudo` first. First find out why a command failed.
- `-R` on `chown` or `chmod` changes everything under a path. Check the path twice.

## License

This project is licensed under the [MIT License](LICENSE).

## Contributor
**Name:** Tehreem Rana  
**Program:** BS Software Engineering (BSSE) – Batch 2025  
**LinkedIn:** [https://www.linkedin.com/in/tehreem22/](https://www.linkedin.com/in/tehreem22/)

## Notes
* Feel free to explore and give it a ⭐ if you like it!
