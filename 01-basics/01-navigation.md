# 01-01 Navigation: Where Am I and How Do I Move?

Linux has **one tree**. The top is `/` (called root). There are no `C:` or `D:` drives.

```text
/
├── home/
│   └── user/
│       ├── notes.txt
│       └── project/
├── etc/
└── var/
```

- **Absolute path** starts from `/`. Example: `/home/user/notes.txt`
- **Relative path** starts from where you are now. Example: `project/notes.txt`

## pwd — where am I?

```bash
pwd
```
What it does: prints your current folder. Example output: `/home/tehreem`

## ls — what is here?

```bash
ls
```
What it does: lists names of files and folders.

```bash
ls -l
```
What it does: long list. Shows permissions, owner, group, size, date, name.

```bash
ls -a
```
What it does: also shows hidden files (names that start with a dot).

```bash
ls -lh
```
What it does: long list with readable sizes (KB, MB).

```bash
ls -la
```
What it does: long list including hidden files.

```bash
ls -ld foldername
```
What it does: shows the folder itself, not what is inside it.

## cd — go to another folder

```bash
cd /home/user
```
What it does: goes to an absolute path.

```bash
cd project
```
What it does: goes into `project` inside the current folder (relative path).

```bash
cd /
```
What it does: goes to the top of the tree.

## Three special shortcuts

| Symbol | Meaning | Example |
|---|---|---|
| `.` | Current folder | `ls .` lists the current folder |
| `..` | Parent folder (one level up) | `cd ..` goes up one level |
| `~` | Your home folder | `cd ~` goes to `/home/yourname` |

```bash
cd ..
```
What it does: goes up one level.

```bash
cd ../..
```
What it does: goes up two levels.

```bash
cd ~
```
What it does: goes to your home folder.

```bash
cd
```
What it does: also goes to your home folder (no path = home).

```bash
ls ~
```
What it does: lists your home folder from anywhere.

```bash
./script.sh
```
What it does: runs `script.sh` from the current folder. `./` means "look in this folder".

Easy memory: `.` = here, `..` = one up, `~` = home.

## `/` and `/root` are not the same

- `/` = top of the whole tree
- `/root` = home folder of the root (admin) user


Next: `02-create-copy-move-delete.md`
