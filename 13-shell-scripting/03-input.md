# 13-03 Input

Three ways to give input to a script: **ask the user** (`read`), **arguments** (`$1 $2`), and **files / pipes**.

## 1. read — keyboard input

```text
read variable
```

```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Welcome $name"
```

| Option | Meaning |
|---|---|
| `-p "text"` | Show a prompt on the same line |
| `-s` | Silent: input is hidden (passwords) |
| `-n 1` | Read only 1 character |
| `-t 5` | Time out after 5 seconds |
| `-a arr` | Read words into an array |

```bash
read -p "Age: " age
read -s -p "Password: " pw
echo
read -n 1 -p "Continue (y/n)? " ans
read -t 5 -p "Quick, answer: " x
```

Many values at once:

```bash
read a b c
```
Input `10 20 30` gives `a=10`, `b=20`, `c=30`. Extra words go to the last variable.

No variable name: the input goes into `$REPLY`.

```bash
read
echo "You typed: $REPLY"
```

## 2. Command-line arguments

Run: `./greet.sh Tehreem 20`

| Variable | Meaning | Value here |
|---|---|---|
| `$0` | Script name | `./greet.sh` |
| `$1` | First argument | `Tehreem` |
| `$2` | Second argument | `20` |
| `$#` | Number of arguments | `2` |
| `$@` | All arguments | `Tehreem 20` |

```bash
#!/bin/bash
echo "Script: $0"
echo "Name: $1"
echo "Age: $2"
echo "Total arguments: $#"
echo "All: $@"
```

Show help when arguments are missing:

```bash
#!/bin/bash
if [ $# -ne 2 ]; then
  echo "Usage: $0 name age"
  exit 1
fi
```

Move to the next argument with `shift` (`$2` becomes `$1`).

## 3. Input from a file or a pipe

```bash
while read line
do
  echo "Line: $line"
done < names.txt
```
What it does: reads `names.txt` one line at a time.

```bash
echo "hello" | read word      # does not keep the value (pipe runs in a sub-shell)
```
Use command substitution instead: `word=$(echo "hello")`.

Next: `04-output.md`
