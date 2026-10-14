# 06-02 Services with systemctl and journalctl

A **service** is software that runs in the background (nginx = web server, ssh = remote access, cron = scheduler).
`systemd` manages services. You talk to it with `systemctl`.

## Check status

```bash
systemctl status nginx
```
What it does: shows if the service is running.

- `active (running)` = up
- `inactive (dead)` = not running
- `failed` = failed to start or stopped by error

## Start, stop, restart, reload

```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
```

| Command | What it does |
|---|---|
| `start` | Start now (does not survive a reboot) |
| `stop` | Stop now |
| `restart` | Stop then start |
| `reload` | Re-read config without stopping (not every service supports it) |

## Enable and disable (boot behaviour)

```bash
sudo systemctl enable nginx
sudo systemctl disable nginx
sudo systemctl enable --now nginx
sudo systemctl disable --now nginx
```

| Command | What it does |
|---|---|
| `enable` | Start automatically at boot |
| `disable` | Do not start at boot (does not stop a running service) |
| `enable --now` | Enable and start right now |
| `disable --now` | Disable and stop right now |

## List and check

```bash
systemctl list-units --type=service
systemctl list-unit-files --type=service
systemctl is-active nginx
systemctl is-enabled nginx
```

| Command | What it does |
|---|---|
| `list-units` | Services currently loaded/active |
| `list-unit-files` | All service files and enabled state |
| `is-active` | Prints `active` or not (good for scripts) |
| `is-enabled` | Prints `enabled` or not |

## Logs

```bash
journalctl -u nginx
journalctl -u nginx -n 50
journalctl -u nginx -f
```
- `-u` = unit (service name)
- `-n 50` = last 50 entries
- `-f` = follow live

## Website not working? Follow this path

1. `sudo systemctl status nginx`
2. If stopped: `sudo systemctl start nginx`
3. If failed: `sudo journalctl -u nginx -n 50`
4. `ps aux | grep nginx`
5. `top`

## Process vs service

| Term | Meaning |
|---|---|
| Process | One running program with a PID |
| Service | A managed background unit (`nginx.service`). It can have many processes |
| `systemctl` | Controls services |
| `journalctl` | Reads service logs |


Next: `../07-environment/01-variables-path-bashrc.md`
