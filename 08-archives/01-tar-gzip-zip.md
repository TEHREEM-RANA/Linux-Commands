# 08-01 Archives and Compression: tar, gzip, zip

- **Archive** = many files into one file (`tar`).
- **Compress** = make it smaller (`gzip`).
- `tar.gz` = both. `zip` = both in one format.

## tar flags

| Flag | Meaning |
|---|---|
| `c` | Create |
| `x` | Extract |
| `t` | List contents |
| `v` | Verbose (show files) |
| `f` | Archive file name |
| `z` | Use gzip |

Build commands from the flags. Do not memorise them as noise.

## tar (archive only)

```bash
tar -cf project.tar project/
```
What it does: puts the `project` folder into `project.tar`.

```bash
tar -tf project.tar
```
What it does: lists what is inside without extracting.

```bash
tar -xf project.tar
```
What it does: extracts the archive.

```bash
tar -cvf project.tar project/
tar -xvf project.tar
```
Same, but prints each file.

```bash
ls -lh project.tar
```
What it does: shows the archive size.

## gzip (compress)

```bash
gzip project.tar
```
What it does: creates `project.tar.gz` and removes the original `project.tar`.

```bash
gunzip project.tar.gz
```
What it does: gives back `project.tar`.

## tar.gz (do both at once)

```bash
tar -czf project.tar.gz project/
tar -xzf project.tar.gz
```
Other formats like `.tar.bz2` and `.tar.xz` use the same idea with another compression.

## zip

```bash
zip -r project.zip project/
unzip project.zip
unzip project.zip -d extracted/
unzip -l project.zip
```

| Command | What it does |
|---|---|
| `zip -r project.zip project/` | Zip a folder (`-r` = recursive) |
| `unzip project.zip` | Extract |
| `unzip project.zip -d extracted/` | Extract into the `extracted` folder |
| `unzip -l project.zip` | List without extracting |

## Compare

| Command | Archive? | Compress? |
|---|---|---|
| `tar` | Yes | No |
| `gzip` | No | Yes |
| `tar.gz` | Yes | Yes |
| `zip` | Yes | Yes |

## Worked example

```bash
mkdir project
touch project/app.py project/config.py project/index.html
tar -cf project.tar project/
tar -tf project.tar
gzip project.tar
gunzip project.tar.gz
tar -xf project.tar
tar -czf project.tar.gz project/
tar -xzf project.tar.gz
zip -r project.zip project/
unzip project.zip
```
`unzip` may ask before overwriting files. Answer `A` (all) or `N` (none), or delete the extracted copy first.


Next: `../09-cron/01-cron.md`
