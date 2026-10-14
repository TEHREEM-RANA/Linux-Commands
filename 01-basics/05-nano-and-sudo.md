# 01-05 nano (Text Editor) and sudo (Admin Rights)

## nano — edit a file in the terminal

```bash
nano notes.txt
```
What it does: opens `notes.txt`. If the file does not exist, nano creates it when you save.

| Keys | What it does |
|---|---|
| `Ctrl + O`, then Enter | Save (write out) |
| `Ctrl + X` | Exit nano (it asks to save if you changed something) |
| `Ctrl + K` | Cut the current line |
| `Ctrl + U` | Paste the cut line |
| `Ctrl + W` | Search for a word |

Used later for: shell scripts (`nano hello.sh`), cron jobs, and Nginx pages (`sudo nano /var/www/html/index.html`).

## sudo — run one command as administrator

```bash
sudo apt update
```
What it does: runs `apt update` with admin (root) rights. It asks for **your** password.

- `sudo` does not make you root permanently. It gives higher rights to **one** command.
- Only users in the `sudo` group can use it (see `../03-users-and-groups/01-users.md`).
- Do not use `sudo` first when something fails. First find out why. See `../04-permissions/05-fix-permission-errors.md`.

Next: `../02-system-info/01-user-terminal-date-info.md`
