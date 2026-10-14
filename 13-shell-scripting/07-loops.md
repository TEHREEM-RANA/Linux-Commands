# 13-07 Loops: for, while, until, select

A loop repeats commands.

## for — repeat for each item

```bash
for fruit in apple mango kiwi
do
  echo "Fruit: $fruit"
done
```

Numbers:

```bash
for i in 1 2 3 4 5
do
  echo "Number $i"
done

for i in {1..5}
do
  echo "Number $i"
done
```
`{1..5}` means 1 to 5. Step of 2: `{1..10..2}`.

C-style:

```bash
for ((i=1; i<=5; i++))
do
  echo "Count $i"
done
```

Over files:

```bash
for file in *.txt
do
  echo "Found: $file"
done
```

Over an array (see `08-arrays.md`):

```bash
fruits=(apple mango kiwi)
for f in "${fruits[@]}"
do
  echo "$f"
done
```

## while — repeat while the condition is true

```bash
count=1
while [ $count -le 3 ]
do
  echo "Round $count"
  count=$((count + 1))
done
```

Repeat while the user says yes:

```bash
input="yes"
while [[ $input = "yes" ]]
do
  echo "Working..."
  read -p "Again (yes/no)? " input
done
```

Read a file line by line:

```bash
while read line
do
  echo "$line"
done < names.txt
```

## until — repeat until the condition becomes true

```bash
count=1
until [ $count -gt 3 ]
do
  echo "Round $count"
  count=$((count + 1))
done
```
`while` runs while the test is true. `until` runs while the test is false.

## break and continue

| Word | What it does |
|---|---|
| `break` | Leaves the loop completely |
| `continue` | Skips the rest of this round, goes to the next one |

```bash
for i in 1 2 3 4 5
do
  if [ $i -eq 2 ]; then
    continue        # skip 2
  fi
  if [ $i -eq 4 ]; then
    break           # stop at 4
  fi
  echo $i           # prints 1 and 3
done
```

## select — automatic numbered menu

```bash
PS3="Choose a number: "
select item in Apple Mango Exit
do
  case "$item" in
    Apple) echo "You chose Apple" ;;
    Mango) echo "You chose Mango" ;;
    Exit)  break ;;
    *)     echo "Invalid choice" ;;
  esac
done
```
- `PS3` is the prompt text.
- `select` repeats until you use `break`.

## Infinite loop

```bash
while true
do
  echo "Press Ctrl + C to stop"
  sleep 1
done
```

Next: `08-arrays.md`
