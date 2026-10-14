# 04-03 chown and chgrp — Owner and Group

## chown — change owner

```bash
sudo chown tehreem file.txt
```
What it does: changes the owner only.

```bash
sudo chown tehreem:students file.txt
```
What it does: changes owner and group.

```bash
sudo chown :students file.txt
```
What it does: changes the group only.

```bash
sudo chown -R tehreem:students project/
```
What it does: changes everything inside `project/` (recursive).

Use your **real** username. Do not assume "tehreem" exists. Use whatever `whoami` shows:

```bash
sudo chown $(whoami) report.txt
```

Changing ownership usually needs `sudo`.

**Danger of `-R`:** it changes every file and subfolder under the path. A wrong path (like `/`) can break access for other users or the system.

## chgrp — change group

```bash
sudo chgrp students report.txt
sudo chgrp -R students project/
```
What it does: changes the group only. It never changes the owner or the `rwx` permissions.

## chown vs chgrp vs chmod

| Command | What it changes |
|---|---|
| `chmod` | What they can do (permission bits) |
| `chown` | Who owns it (and optionally the group) |
| `chgrp` | The group only |

## Example

```bash
sudo adduser tehreem
sudo groupadd developers
sudo usermod -aG developers tehreem
sudo touch /opt/project.txt
sudo chown tehreem:developers /opt/project.txt
sudo chmod 640 /opt/project.txt
ls -l /opt/project.txt
```
Result: owner `tehreem` = read+write, group `developers` = read, others = nothing.


Next: `04-umask.md`
