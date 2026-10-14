# 13-10 Exit Status and Comments

## Exit status

Every command returns a number when it finishes.

- `0` = success
- `1` to `255` = failure

```bash
ls /home
echo $?          # 0
ls /nofolder
echo $?          # 2
```
`$?` holds the status of the **last** command.

| Code | Meaning |
|---|---|
| 0 | Success |
| 1 | General error |
| 2 | Misuse of a command |
| 126 | Command not executable |
| 127 | Command not found |

## Use the status in a script

```bash
mkdir test && echo "OK"          # second runs only if the first succeeds
cd /xyz || echo "Failed"         # second runs only if the first fails

if [ $? -eq 0 ]; then
  echo "Success"
fi
```

## exit — end the script with a status

```bash
#!/bin/bash
if [ $# -ne 2 ]; then
  echo "Usage: $0 num1 num2"
  exit 1          # stop with an error status
fi
echo "Arguments are fine"
exit 0            # stop with success
```
Check the script's own status after it runs: `./script.sh; echo $?`

## Comments

A comment is a note the shell ignores.

```bash
#!/bin/bash
# Calculator program
# Author: Tehreem
x=5            # first number (a comment can follow a command)

: '
This is a
multi-line comment
'
echo $x
```

- `#` starts a single-line comment.
- The shebang `#!/bin/bash` on line 1 is **not** a comment. It is a special line.
- Multi-line trick: `: ' ... '`. Another way is a here-doc: `<<COMMENT ... COMMENT`.
- Use comments to explain logic, help teammates, and switch off code while testing.

Next: `11-example-menu-calculator.md`
