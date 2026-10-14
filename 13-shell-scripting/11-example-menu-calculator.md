# 13-11 Full Example: Menu Calculator

This script puts together everything from this folder: variables, input, output, arithmetic, conditions, `case`, `select` and `while`.

## The flow

`while` → `select` menu → `case` → `read` two numbers → arithmetic → print result → ask again? If `yes`, the loop restarts. Otherwise the program says thank you and ends.

## Code (`calculator.sh`)

```bash
#!/bin/bash
input="yes"
while [[ $input = "yes" ]]
do
  echo "Calculator"
  PS3="Press 1 Add, 2 Sub, 3 Mul, 4 Div: "
  select math in Addition Subtraction Multiplication Division
  do
    case "$math" in
      Addition)       read -p "First no: " n1; read -p "Second no: " n2
                      echo "Answer: $((n1 + n2))"; break;;
      Subtraction)    read -p "First no: " n1; read -p "Second no: " n2
                      echo "Answer: $((n1 - n2))"; break;;
      Multiplication) read -p "First no: " n1; read -p "Second no: " n2
                      echo "Answer: $((n1 * n2))"; break;;
      Division)       read -p "First no: " n1; read -p "Second no: " n2
                      echo "Answer: $(echo "scale=2; $n1/$n2" | bc)"; break;;
      *) echo "Choose 1 to 4 only!!!"; break;;
    esac
  done
  read -p "Calculate again (yes/no)? " input
done
echo "Thank you for using this program"
```

## Run it

```bash
chmod +x calculator.sh
./calculator.sh
```

## What each part does

| Part | Job |
|---|---|
| `while [[ $input = "yes" ]]` | Repeats while the answer is yes |
| `PS3=...` | The prompt text of the menu |
| `select` | Shows a numbered menu automatically |
| `case "$math" in` | Runs the code for the chosen item |
| `;;` | Ends each case |
| `*)` | Handles invalid input |
| `break` | Leaves the `select` menu after one calculation |
| `$((n1 + n2))` | Integer arithmetic |
| `bc` | Division with decimals |
| `read -p` | Asks for input on the same line |
