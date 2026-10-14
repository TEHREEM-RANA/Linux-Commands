# 01-02 Create, Copy, Move, Delete

Analogy: `cp` is a photocopy (the original stays). `mv` is picking it up and putting it somewhere else (only one copy exists).

## Create

```bash
mkdir project
```
What it does: creates a folder named `project`.

```bash
mkdir -p practice/data
```
What it does: creates the parent folder too if it does not exist (`-p` = parents).

```bash
touch notes.txt
```
What it does: creates an empty file.

```bash
touch a.txt b.txt c.log
```
What it does: creates three files in one command.

## Copy

```bash
cp notes.txt notes_backup.txt
```
What it does: copies a file. The original stays.

```bash
cp -r src dest
```
What it does: copies a folder and everything inside it (`-r` = recursive).

## Move or rename

```bash
mv old.txt new.txt
```
What it does: renames `old.txt` to `new.txt`.

```bash
mv notes.log data/
```
What it does: moves the file into the `data` folder.

```bash
mv notes.log data/notes_renamed.log
```
What it does: moves and renames in one step.

## Delete (be careful: no recycle bin)

```bash
rm file.txt
```
What it does: deletes a file.

```bash
rm -r old_folder
```
What it does: deletes a folder and everything inside it.

```bash
rm -f file.txt
```
What it does: forces deletion without asking.

Check your path with `pwd` and `ls` **before** you run `rm -r`.

## Symbolic link (shortcut)

```bash
ln -s file link
```
What it does: creates `link`, a shortcut that points to `file`.

## Full example session

```bash
mkdir project
cd project
touch notes.txt
ls -l
pwd
echo "Hello Linux" > notes.txt
cp notes.txt notes_backup.txt
mv notes_backup.txt archive.txt
cat notes.txt
find . -name "*.txt"
```

Expected end result:

```text
Hello Linux
./notes.txt
./archive.txt
```


Next: `03-view-files-and-output.md`
