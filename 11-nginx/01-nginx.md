# 11-01 Nginx: Put a Web Page Online

Nginx is a web server. Flow: Browser → port 80 → Nginx → files in `/var/www/html`.

## Install and start

```bash
sudo apt update
sudo apt install nginx
sudo systemctl enable --now nginx
```
`enable --now` = start now and at every boot.

## Check it

```bash
systemctl status nginx
systemctl is-active nginx
ps aux | grep nginx
```
You want `active (running)`. Several nginx processes is normal.

## See the default page from the server

```bash
curl http://127.0.0.1
curl http://localhost
curl -I http://127.0.0.1
```
- The first two print the HTML.
- `-I` prints only headers. Look for `HTTP/1.1 200` and `Server: nginx`.

From your laptop, open `http://YOUR_SERVER_IP` in a browser.

## Debug commands

```bash
sudo ss -tlnp | grep ':80'
sudo nginx -t
sudo journalctl -u nginx -n 50
```

| Command | What it does |
|---|---|
| `ss -tlnp \| grep ':80'` | Is something listening on port 80? |
| `nginx -t` | Test the config without applying it |
| `journalctl -u nginx -n 50` | Last 50 log lines |

## Where Nginx keeps things

```text
/etc/nginx/nginx.conf             main config
/etc/nginx/sites-available/       site definitions
/etc/nginx/sites-enabled/         sites that are turned on (links)
/var/www/html/                    default files Nginx serves
```

```bash
ls /etc/nginx/sites-available
ls /etc/nginx/sites-enabled
ls -l /etc/nginx/sites-enabled
```
Enabling a site = making a link. Disabling = removing the link (the file in `sites-available` stays).

## Serve your own page

```bash
ls -l /var/www/html
sudo nano /var/www/html/index.html
```
Put in the file:

```html
<!DOCTYPE html>
<html>
  <head><title>Hello</title></head>
  <body><h1>Hello from Nginx</h1></body>
</html>
```
Then:

```bash
curl http://127.0.0.1
```
No restart is needed for an HTML change.

## Changed the config? Test, then reload

```bash
sudo nginx -t
sudo systemctl reload nginx
sudo systemctl restart nginx
```
Use `reload` first. Use `restart` only if `reload` is not enough.

Do not `chmod 777` the web root. Fix owner or group instead (`www-data` is Nginx's usual user on Ubuntu).

## Page does not load?

1. `systemctl status nginx`: is it running?
2. `sudo nginx -t`: is the config valid?
3. `curl http://127.0.0.1`: does it work on the server?
4. If `curl` works but the browser does not, check the firewall:

```bash
sudo ufw status
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```
Only if you use UFW. Some VPS panels have the firewall in their dashboard instead.


Next: `../12-file-transfer/01-ssh-scp-sftp-rsync.md`
