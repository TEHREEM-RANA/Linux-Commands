# 04-02 chmod — Change Permissions

```text
chmod [options] mode file
```
Only the **owner** (or root) can change permissions.

## Numeric mode (set everything at once)

| Command | Owner | Group | Others | Use |
|---|---|---|---|---|
| `chmod 755 script.sh` | rwx | r-x | r-x | Scripts and shared folders |
| `chmod 644 file.txt` | rw- | r-- | r-- | Normal shared file |
| `chmod 700 private_dir` | rwx | --- | --- | Only owner can use it |
| `chmod 600 secret.txt` | rw- | --- | --- | Private file |
| `chmod 640 file.txt` | rw- | r-- | --- | Owner edits, group reads |

## Symbolic mode (small changes)

Form: **who** (`u g o a`) + **action** (`+` add, `-` remove, `=` set exactly) + **permission** (`r w x`).

| Command | Meaning |
|---|---|
| `chmod u+x script.sh` | Add execute for the owner |
| `chmod +x script.sh` | Add execute (for all) |
| `chmod g+w report.txt` | Add write for the group |
| `chmod g-r report.txt` | Remove read for the group |
| `chmod o-r report.txt` | Remove read for others |
| `chmod o-rwx private.txt` | Remove all access for others |
| `chmod a+x script.sh` | Add execute for everyone |
| `chmod g=rx file.txt` | Set group to exactly r-x |
| `chmod u=rwx,g=rx,o= report.sh` | Set exact mode for each class |

Use **symbolic** for a small change ("just add execute").
Use **numeric** to set the full set at once.

## Example

```bash
touch script.sh
ls -l script.sh
chmod u+x script.sh
ls -l script.sh
./script.sh
```
Change: `-rw-r--r--` → `-rwxr--r--`. Only the owner's `x` changed.

## Demo

```bash
mkdir permission_demo
cd permission_demo
touch file.txt
ls -l
chmod 600 file.txt
ls -l
chmod 644 file.txt
ls -l
chmod 755 file.txt
ls -l
```
- 600: owner read/write, nobody else
- 644: owner read/write, others read only
- 755: owner full, others read + execute

## Why not 777?

`777` = `rwx rwx rwx`. Everyone can read, change and run it. Do not use it just because you got "permission denied". Find out who needs access and give the minimum.

## Common mistakes

- Forgetting that only the owner (or root) can change permissions.
- Thinking `755` is a file size or version number.
- Changing the wrong file. Check with `pwd` and `ls` first.
- Using `chmod 777`.


Next: `03-chown-and-chgrp.md`
