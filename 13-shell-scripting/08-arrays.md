# 13-08 Arrays

An array holds many values in one variable.

## Indexed array (numbered from 0)

```bash
fruits=(apple mango kiwi)
echo "Second fruit: ${fruits[1]}"   # mango (index 1, not 2)
echo "Count: ${#fruits[@]}"         # 3
fruits+=(grape)                     # add an element
echo "All: ${fruits[@]}"            # apple mango kiwi grape
```

| Index | Value |
|---|---|
| 0 | apple |
| 1 | mango |
| 2 | kiwi |
| 3 | grape (after adding) |

In `${#fruits[@]}`: `fruits` = the array, `[@]` = all elements, `#` = count.

| Syntax | Meaning |
|---|---|
| `arr=(a b c)` | Create |
| `declare -a arr` | Declare an indexed array |
| `${arr[0]}` | One element |
| `${arr[@]}` | All elements |
| `${#arr[@]}` | Number of elements |
| `${!arr[@]}` | All indexes |
| `arr+=(d)` | Add at the end |
| `arr[1]="new"` | Change one element |
| `unset arr[1]` | Remove one element |
| `${arr[@]:1:2}` | Slice: 2 elements starting at index 1 |

### Loop over an array

```bash
for f in "${fruits[@]}"
do
  echo "$f"
done
```

### Total, average, highest

```bash
marks=(70 85 90 60 75)
total=0
highest=${marks[0]}
for m in "${marks[@]}"
do
  total=$((total + m))
  if [ $m -gt $highest ]; then
    highest=$m
  fi
done
echo "Total: $total"
echo "Average: $((total / ${#marks[@]}))"
echo "Highest: $highest"
```

## Associative array (keys instead of numbers)

Works like a dictionary: key → value. Needs bash 4+.

```bash
declare -A age
age[tehreem]=20
age[sara]=22
echo "Tehreem is ${age[tehreem]}"
```

Loop over the keys with `${!age[@]}`:

```bash
for name in "${!age[@]}"
do
  echo "$name is ${age[$name]}"
done
```

| Syntax | Meaning |
|---|---|
| `declare -A m` | Declare (required for associative arrays) |
| `m[key]=value` | Set |
| `${m[key]}` | Get |
| `${!m[@]}` | All keys |
| `${m[@]}` | All values |
| `${#m[@]}` | Number of pairs |

Next: `09-functions.md`
