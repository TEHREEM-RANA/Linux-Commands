# 04-01 Read Permissions

Linux is multi-user. Permissions decide who can read, change or run a file.
Linux asks: "Can **this person** touch this file?"

## Three kinds of people

| Class | Letter | Meaning |
|---|---|---|
| Owner | `u` | The person who owns the file |
| Group | `g` | The group the file belongs to |
| Others | `o` | Everyone else |
| All | `a` | Owner + group + others (used in `chmod`) |

## Three permissions

| Letter | Meaning | Example |
|---|---|---|
| `r` | Read | `cat file.txt` |
| `w` | Write (change) | `nano file.txt` |
| `x` | Execute (run) | `./script.sh` |
| `-` | Not given | |

## See permissions

```bash
ls -l
```
Example line:

```text
-rw-r--r-- 1 tehreem students 1250 Sep 22 10:30 report.txt
```

| Field | Value | Meaning |
|---|---|---|
| Permissions | `-rw-r--r--` | Type + owner + group + others |
| Links | `1` | Number of hard links |
| Owner | `tehreem` | The file's owner |
| Group | `students` | The file's group |
| Size | `1250` | Bytes |
| Modified | `Sep 22 10:30` | Last change time |
| Name | `report.txt` | File name |

```bash
ls -ld dirname
```
What it does: shows the **directory's own** permissions (not its contents).

## Read the string `-rwxr-xr--`

| Part | Characters | Meaning |
|---|---|---|
| Type | `-` | Regular file |
| Owner | `rwx` | Read, write, execute |
| Group | `r-x` | Read and execute |
| Others | `r--` | Read only |

First character: `-` file, `d` directory, `l` symbolic link.
The order is always **Owner → Group → Others**, 3 characters each.

## Which set does Linux use?

```text
Is the user the owner?     YES -> use OWNER permissions
Is the user in the group?  YES -> use GROUP permissions
Otherwise                  -> use OTHERS permissions
```
Linux does not add them together. Only one set is used.

## Files vs directories

| Permission | On a file | On a directory |
|---|---|---|
| `r` | Read the contents | List the contents (`ls`) |
| `w` | Change the contents | Create, delete, rename items inside |
| `x` | Run as a program | Enter the directory (`cd`) |

```bash
ls directory        # needs r on 'directory'
cd directory        # needs x on 'directory'
touch directory/new # needs w AND x on 'directory'
```

Read is not execute. You can see a script's text but not run it unless it has `x`.

## Numbers (octal)

`r = 4`, `w = 2`, `x = 1`, `- = 0`. Add them for each class.

| Symbols | Calculation | Number |
|---|---|---|
| `rwx` | 4+2+1 | 7 |
| `rw-` | 4+2 | 6 |
| `r-x` | 4+1 | 5 |
| `r--` | 4 | 4 |
| `-wx` | 2+1 | 3 |
| `-w-` | 2 | 2 |
| `--x` | 1 | 1 |
| `---` | 0 | 0 |

Example: `rwx r-x r--` = `7 5 4` = mode `754`.


Next: `02-chmod.md`
