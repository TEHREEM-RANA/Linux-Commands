# 04-05 Fix Permission Errors

Golden rule: **do not use `sudo` first.** First find out why it was denied.

## Investigate step by step

```bash
ls -l            # check file permissions
whoami           # check current user
pwd              # confirm current folder
ls -ld dir       # check directory permissions
id               # check user and groups
```

## Error table

| Error | Likely cause | Check with |
|---|---|---|
| `Permission denied` | You do not have the needed r/w/x | `ls -l`, `whoami` |
| `Operation not permitted` | You need ownership or higher rights | `ls -l`, `id` |
| `No such file or directory` | Wrong path, typo or missing file | `pwd`, `ls` |
| `command not found` | Typo, missing package, or not in PATH | `which <command>` |

## Common cases

**`./script.sh` does not run**

```bash
ls -l script.sh
chmod u+x script.sh
./script.sh
```
Check execute permission first.

**You can see a folder name but cannot enter it**
The folder's `x` bit is missing:

```bash
ls -ld foldername
chmod u+x foldername
```

**Typo**

```bash
chmod g+w repot.txt
```
Gives `No such file or directory`. The file name is wrong. Check names with `ls`.

## Worked example: team access

```bash
sudo adduser tehreem
sudo adduser guest
sudo groupadd developers
sudo usermod -aG developers tehreem
sudo usermod -aG developers guest
sudo touch /opt/project.txt
sudo chown tehreem:developers /opt/project.txt
sudo chmod 640 /opt/project.txt
ls -l /opt/project.txt
```

| Person | Role | Access |
|---|---|---|
| tehreem | owner | read + write |
| guest | group member | read |
| anyone else | others | none |


Next: `../05-packages/01-apt.md`
