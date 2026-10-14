# 12-01 Move Files: ssh, scp, sftp, rsync, FileZilla

SSH gives you a shell. File transfer tools give you files. All of them use port 22 (SSH). Do not use plain FTP (port 21); it sends passwords in clear text.

## ssh (recap)

```bash
ssh tehreem@203.0.113.10
ssh -i ~/.ssh/id_rsa tehreem@203.0.113.10
```

## Laptop → server

```bash
scp page.html tehreem@203.0.113.10:/var/www/html/
```
What it does: one-shot copy of one file.

```bash
scp -r site/ tehreem@203.0.113.10:/var/www/html/
```
What it does: copies a whole folder (`-r`).

```bash
rsync -av page.html tehreem@203.0.113.10:/var/www/html/
rsync -av site/ tehreem@203.0.113.10:/var/www/html/
```
What it does: copies, and next time only sends what changed. `-a` keeps permissions and times, `-v` shows progress.

`site/` (with slash) copies the **contents**. `site` (no slash) may create an extra `site/` folder on the server.

```bash
sftp tehreem@203.0.113.10
```
What it does: opens an interactive session. Inside it:

| sftp command | What it does |
|---|---|
| `put index.html` | Upload a file |
| `get index.html` | Download a file |
| `ls` | List remote files |
| `cd` | Change remote folder |
| `bye` | Quit |

## Server → laptop

```bash
scp tehreem@203.0.113.10:/var/www/html/index.html .
rsync -av tehreem@203.0.113.10:/var/www/html/index.html .
```
The `.` means "to the current folder".

## Using a key

```bash
scp -i ~/.ssh/id_rsa page.html tehreem@203.0.113.10:/var/www/html/
sftp -i ~/.ssh/id_rsa tehreem@203.0.113.10
rsync -av -e "ssh -i ~/.ssh/id_rsa" page.html tehreem@203.0.113.10:/var/www/html/
```

## Which one to use?

| Tool | Best for |
|---|---|
| FileZilla | Visual folders, occasional uploads |
| scp | One file or a small folder, quickly |
| rsync | A project folder you update again and again |

## FileZilla (graphical)

1. Install the **client** from filezilla-project.org.
2. File → Site Manager (or Quickconnect).
3. Fill in:

| Field | Value |
|---|---|
| Protocol | SFTP |
| Host | Your server IP |
| Port | 22 |
| User | `root` or `tehreem` (what you use for SSH) |
| Password / key | Same as SSH |

4. Connect and accept the host key.
5. Drag a file right to upload. Drag left to download.

If it asks for FTP, change it to SFTP.

## After an upload: check permissions

A file owned by root with mode `600` may not be readable by Nginx (`www-data`). Fix on the server:

```bash
ls -l /var/www/html
sudo chown www-data:www-data /var/www/html/index.html
sudo chmod 644 /var/www/html/index.html
```
Do not use `777`.


Next: `../13-shell-scripting/01-first-script.md`
