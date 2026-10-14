# 13-04 Output

## echo — print text

```text
echo [options] "text"
```

| Option / symbol | Meaning |
|---|---|
| `-n` | No new line at the end |
| `-e` | Allow escapes: `\n` new line, `\t` tab |
| `" "` | Double quotes: variables are expanded |
| `' '` | Single quotes: printed exactly |

```bash
echo "Hello World"
echo -n "No newline"
echo -e "Line1\nLine2"
echo -e "Name\tAge"
echo "Hi $USER"        # expands the variable
echo 'Hi $USER'        # prints literally
```

## printf — formatted output

```bash
printf "Name: %s\n" "Tehreem"
printf "Age: %d\n" 20
printf "Pi: %.2f\n" 3.14159
```

| Code | Meaning |
|---|---|
| `%s` | Text |
| `%d` | Whole number |
| `%f` | Decimal number (`%.2f` = 2 digits after the point) |
| `\n` | New line |

`printf` does not add a new line by itself. Add `\n`.

## Redirection: send output to a file

| Symbol | Meaning | Example |
|---|---|---|
| `>` | Write to a file (overwrites old content) | `echo "hi" > a.txt` |
| `>>` | Add to the end of a file | `echo "log" >> a.txt` |
| `2>` | Send errors to a file | `ls /nofolder 2> err.txt` |
| `2>&1` | Send errors to the same place as normal output | `cmd >> log.txt 2>&1` |
| `<` | Take input from a file | `sort < names.txt` |
| `/dev/null` | A bin that throws everything away | `cmd > /dev/null 2>&1` |

## Pipe

```bash
ls -l | grep txt
ps aux | grep nginx
```
A pipe sends the output of one command to the next command.

## Here-document (many lines in one go)

```bash
cat << EOF
Name: Tehreem
Program: BSSE
EOF
```
What it does: prints every line up to the word `EOF`.

## Show on screen and save to a file together

```bash
echo "Backup done" | tee -a log.txt
```
`tee` shows the text and also saves it. `-a` means add (do not overwrite).

Next: `05-arithmetic.md`
