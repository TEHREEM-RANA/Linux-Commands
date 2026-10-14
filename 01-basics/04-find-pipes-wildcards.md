# 01-04 Find, Wildcards, Pipes

## Wildcard `*`

The star matches any characters.

```bash
ls *.txt
```
What it does: lists every file that ends in `.txt`.

## find — search by name

```bash
find . -name "*.txt"
```
What it does: searches the current folder (`.`) and everything below it for names ending in `.txt`.

```bash
find /home -name "notes.txt"
```
What it does: searches inside `/home` for a file called `notes.txt`.

| Option | Meaning |
|---|---|
| `-name` | Match by file name |
| `-type` | Match by type (`f` = file, `d` = directory) |

```bash
find . -type d
```
What it does: lists only folders.

## Pipe `|`

A pipe takes the output of one command and gives it to the next command.

```bash
ps aux | grep nginx
```
What it does: gets all processes, then keeps only lines that contain `nginx`.

```bash
apt list --installed | grep nginx
```
What it does: checks if a package is installed.

`grep word` prints only the lines that contain `word`.

## Run two commands in order

```bash
sudo apt update && sudo apt upgrade
```
What it does: `&&` runs the second command **only if** the first one succeeded.

```bash
cd /xyz || echo "Failed"
```
What it does: `||` runs the second command **only if** the first one failed.


Next: `05-nano-and-sudo.md`
