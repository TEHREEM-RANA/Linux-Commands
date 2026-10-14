# 15-02 Common Errors and First Checks

| Error message | Likely cause | Check with |
|---|---|---|
| `Permission denied` | Missing r/w/x bit | `ls -l`, `whoami` |
| `Operation not permitted` | Need ownership or higher rights | `ls -l`, `id` |
| `No such file or directory` | Wrong path, typo, missing file | `pwd`, `ls` |
| `command not found` | Typo, missing package, not in PATH | `which name`, `echo $PATH` |
| `bash: x: readonly variable` | You changed a `readonly` variable | `declare -p x` |
| `./script.sh: Permission denied` | No execute bit | `chmod u+x script.sh` |
| `no crontab for user` | You have no cron jobs yet | `crontab -e` |
| Browser cannot open the site, `curl` works | Firewall blocks port 80 | `sudo ufw status` |

## Mistakes to avoid

- `x = 5` in a script (spaces). Use `x=5`.
- `export PATH="/new/folder"` (replaces PATH). Use `export PATH="$PATH:/new/folder"`.
- `chmod 777` to "fix" things.
- `kill -9` as the first choice. Try `kill` first.
- `rm -r` or `chown -R` before checking the path with `pwd` and `ls`.
- Using `sudo apt update` and thinking Linux is updated. It only refreshes the list.
- `usermod -G` without `-a`. It can remove old groups.

## Debug order for a service

`systemctl status` → `journalctl -u name -n 50` → `ps aux | grep name` → `top`
