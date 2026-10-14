# 13-02 Variables

A variable is a named place in memory that stores a value.

## Rules

- Create: `name=value` — **no spaces** around `=`
- Use: `$name` or `${name}`
- Names can have letters, digits and underscore. They cannot start with a digit. They are **case sensitive** (`Age` and `age` are different).
- Bash stores everything as text. Numbers act as integers only inside arithmetic.

```bash
#!/bin/bash
name="Tehreem"
age=20
echo "Name: $name"
echo "Age: $age"
echo "User: $USER"
echo "Home: $HOME"
```

| Command | What it does |
|---|---|
| `unset name` | Removes a variable |
| `readonly PI=3.14` | Makes a constant (cannot be changed or unset) |
| `declare -p name` | Shows the type and value of a variable |

## Common errors

| Wrong | Right | Why |
|---|---|---|
| `x = 5` | `x=5` | No spaces around `=` |
| `$x=5` | `x=5` | No `$` on the left |
| `name=Tehreem Rana` | `name="Tehreem Rana"` | Quote text with spaces |

## Kinds of variables

| Kind | Examples |
|---|---|
| User variables | `age=20`, `name="Tehreem"` |
| Environment variables | `HOME`, `USER`, `PATH`, `PWD`, `SHELL` (child processes inherit them when exported) |
| Special variables | `$0` script name, `$1`..`$9` arguments, `$#` argument count, `$@` all arguments, `$?` exit status, `$$` process ID |

## Quotes

| Quote | Behaviour | Example output |
|---|---|---|
| `"double"` | Variables are expanded | `echo "Hi $USER"` → `Hi tehreem` |
| `'single'` | Printed exactly as written | `echo 'Hi $USER'` → `Hi $USER` |

Always quote `"$var"`. Without quotes, a value with spaces is split into many words and can break your script.

## Command substitution

Save the output of a command in a variable:

```bash
today=$(date +%F)
echo "Today is $today"
files=$(ls | wc -l)
echo "Files here: $files"
```

## Useful tricks

| Trick | Meaning |
|---|---|
| `${#name}` | Length of the text |
| `"$a$b"` | Join two variables |
| `${x:-default}` | Use `default` if `x` is empty |
| `-z "$x"` | Test: is `x` empty? |
| `-n "$x"` | Test: is `x` not empty? |

```bash
name="Tehreem"
echo ${#name}          # 7
echo ${nick:-friend}   # friend (nick is empty)
```

## Variable types in Bash

| Type | Declare / example | Notes |
|---|---|---|
| String | `name="Tehreem"` | Default type |
| Integer | `declare -i n=5` | Arithmetic works directly: `n=n+2` |
| Constant | `readonly PI=3.14` | Cannot be changed or unset |
| Indexed array | `declare -a f=(a b c)` | Index starts from 0 (see `08-arrays.md`) |
| Associative array | `declare -A m` | Key-value pairs, bash 4+ (see `08-arrays.md`) |
| Environment | `export VAR=value` | Visible to child processes |

### Integer variable

```bash
declare -i n=5
n=n*2
echo "Integer: $n"     # Integer: 10
```
`-i` means integer, so `n=n*2` does real arithmetic (5 x 2 = 10).
`declare -i n=abc` stores `0`, because text becomes 0 in an integer variable.

### Read-only variable

```bash
readonly PI=3.14
echo "PI = $PI"
PI=5                   # bash: PI: readonly variable
```
Use it for constants such as `readonly MAX_USERS=100`.

## Scope: global, local, exported

```bash
g="global"
show(){
  local l="local"
  echo "$g $l"        # global variable works inside the function
}
show
echo "$l"             # empty: local is not available outside

export MODE=test
bash -c 'echo $MODE'  # prints test
```

| Scope | Meaning |
|---|---|
| Global | Available everywhere in the script |
| Local | Declared with `local` inside a function. Not available outside it |
| Exported | `export VAR` passes the variable to child processes |

Next: `03-input.md`
