# 13-09 Functions

A function is a block of commands with a name. Write it once, call it many times.

## Create and call

```bash
#!/bin/bash
greet() {
  echo "Hello from a function"
}

greet
greet
```
Define the function **before** you call it.

## Arguments

Inside a function `$1`, `$2`, ... are the function's own arguments.

```bash
greet() {
  echo "Hello $1, you are $2 years old"
}
greet "Tehreem" 20
```

## Local variables

```bash
show() {
  local x="inside"
  echo "$x"
}
show
echo "$x"      # empty: local is not visible outside
```

## Return a value

`return` gives a **status number** (0-255), like an exit status.

```bash
is_even() {
  if [ $(($1 % 2)) -eq 0 ]; then
    return 0
  else
    return 1
  fi
}

if is_even 4; then
  echo "Even"
fi
echo $?
```

To return text or a big number, print it and capture it:

```bash
add() {
  echo $(($1 + $2))
}
result=$(add 5 3)
echo "Sum: $result"
```

## Functions with case (menu style)

```bash
add() { echo "Answer: $(($1 + $2))"; }
sub() { echo "Answer: $(($1 - $2))"; }

read -p "Choose (add/sub): " op
read -p "First: " a
read -p "Second: " b
case "$op" in
  add) add $a $b ;;
  sub) sub $a $b ;;
  *)   echo "Invalid" ;;
esac
```

Next: `10-exit-status-and-comments.md`
