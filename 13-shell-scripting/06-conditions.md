# 13-06 Conditions: if, elif, else, case

## if / elif / else

Order: `if` condition → `then` commands → `elif` another condition → `else` default → `fi` closes the if.

```bash
age=25
if [ $age -ge 60 ]
then
  echo "Senior"
elif [ $age -ge 18 ]
then
  echo "Adult"
else
  echo "Minor"
fi
```

Short form: `if [ $age -ge 18 ]; then echo "Adult"; fi`

Spaces inside `[ ]` are required: `[ $age -ge 18 ]`, not `[$age -ge 18]`.

## Test operators

### Numbers

| Test | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |
| `-lt` | Less than |
| `-le` | Less than or equal |

### Text (strings)

| Test | Meaning |
|---|---|
| `[ "$a" = "$b" ]` | Equal |
| `[ "$a" != "$b" ]` | Not equal |
| `[ -z "$a" ]` | Empty |
| `[ -n "$a" ]` | Not empty |
| `[[ $a = "yes" ]]` | Equal (double brackets) |
| `[[ $n =~ ^-?[0-9]+$ ]]` | Text is a whole number (pattern match) |

### Files and folders

| Test | Meaning |
|---|---|
| `-e path` | Exists |
| `-f path` | Is a regular file |
| `-d path` | Is a directory |
| `-r path` | Readable |
| `-w path` | Writable |
| `-x path` | Executable |

```bash
if [ -f report.txt ]; then
  echo "report.txt exists"
else
  echo "report.txt is missing"
fi

if [ -d /var/log ]; then
  echo "folder found"
fi
```

## Combine conditions

| Symbol | Meaning |
|---|---|
| `&&` | AND: both must be true |
| `\|\|` | OR: one must be true |
| `!` | NOT |

```bash
if [ $age -ge 18 ] && [ $age -lt 60 ]; then
  echo "Adult"
fi

if [[ $age -lt 18 || $age -ge 60 ]]; then
  echo "Not working age"
fi

if [ ! -f data.txt ]; then
  echo "data.txt is missing"
fi
```

## Run a command only if another worked

```bash
mkdir test && echo "OK"          # second runs only if the first succeeds
cd /xyz || echo "Failed"         # second runs only if the first fails
```

## Check a command's result

```bash
ls /home
if [ $? -eq 0 ]; then
  echo "Success"
fi
```
`$?` is the exit status of the last command (0 = success). See `10-exit-status-and-comments.md`.

## case — match one choice from many

```bash
read -p "Choose (a/b/q): " c
case "$c" in
  a) echo "You chose A" ;;
  b) echo "You chose B" ;;
  q) echo "Bye" ;;
  *) echo "Invalid choice" ;;
esac
```

- Each choice ends with `;;`.
- `*` matches anything else (invalid input).
- `esac` closes the case.
- Use `|` for several patterns: `y|Y|yes) echo "Yes" ;;`

Next: `07-loops.md`
