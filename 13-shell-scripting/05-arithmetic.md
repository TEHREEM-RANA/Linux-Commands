# 13-05 Arithmetic

Operators: `+  -  *  /  %` (remainder) `**` (power)

| Method | Notes |
|---|---|
| `$(( expression ))` | **Preferred.** Integers only. Variables inside need no `$` |
| `expr 5 + 3` | Spaces are required. Escape the star: `\*` |
| `let c=a+b` | Stores the result in `c` |
| `bc` | Decimal maths |

```bash
a=10; b=3
echo $((a + b))             # 13
echo $((a - b))             # 7
echo $((a * b))             # 30
echo $((a / b))             # 3  (decimals are dropped)
echo $((a % b))             # 1
echo $((a ** 2))            # 100
expr $a + $b                # 13
expr $a \* $b               # 30
let c=a+b
echo $c                     # 13
echo "scale=2; $a/$b" | bc  # 3.33
```

- `$(( ))` gives integers only. `10/3` is `3`, and `7/2` is `3`.
- Use `bc` for decimals. `scale=2` means 2 digits after the point.
- Square root: `echo "sqrt(16)" | bc -l`

## Change a variable

```bash
count=5
count=$((count + 1))     # 6
((count++))              # 7
((count--))              # 6
((count += 10))          # 16
```

## Integer variable

```bash
declare -i n=5
n=n*2
echo $n                  # 10
```

## Compare numbers (used in conditions)

| Test | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |
| `-lt` | Less than |
| `-le` | Less than or equal |

Next: `06-conditions.md`
