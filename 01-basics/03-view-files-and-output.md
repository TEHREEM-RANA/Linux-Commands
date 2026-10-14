# 01-03 View Files and Print Output

## cat — print a whole file

```bash
cat file.txt
```
What it does: prints the full file in the terminal.

```bash
cat file1.txt file2.txt
```
What it does: prints both files, one after the other.

```bash
cat -n file.txt
```
What it does: prints with line numbers.

Create a file with `cat`:

```bash
cat > hello.txt
```
Type your text, then press **Ctrl + D** to save. This **overwrites** the file.

Add to the end of a file:

```bash
cat >> hello.txt
```
Type your text, then press **Ctrl + D**.

`cat` prints everything at once. A file with 50,000 lines will flood the screen. Use `less` for big files.

## less — read a big file page by page

```bash
less /var/log/syslog
```
What it does: opens the file in a scrollable viewer.

| Key | Action |
|---|---|
| Up / Down arrow | Move one line |
| Space | One page down |
| `b` | One page up |
| Enter | One line down |
| `g` | Go to the beginning |
| `G` | Go to the end |
| `/word` then Enter | Search for a word |
| `n` | Next search result |
| `q` | Quit |

Example: open `less server.log`, type `/error`, press Enter, then press `n` for the next match.

`cat` = quick print for small files. `less` = explore big files.

## head and tail — first and last lines

```bash
head -n 5 file.txt
```
What it does: shows the first 5 lines.

```bash
tail -n 5 file.txt
```
What it does: shows the last 5 lines.

```bash
tail -f file.log
```
What it does: keeps watching the file and prints new lines as they arrive (`-f` = follow).

## echo — print text

```bash
echo "Hello World"
```
What it does: prints the text.

```bash
echo -n "No newline"
```
What it does: prints without a new line at the end.

```bash
echo -e "Line1\nLine2"
```
What it does: `-e` allows escapes. `\n` = new line, `\t` = tab.

```bash
echo "Hi $USER"
echo 'Hi $USER'
```
What it does: double quotes **expand** the variable (prints your name). Single quotes print the text exactly (`Hi $USER`).

## Write output to a file

| Symbol | Meaning | Example |
|---|---|---|
| `>` | Write to a file (overwrites old content) | `echo "hi" > a.txt` |
| `>>` | Add to the end of a file | `echo "hi" >> a.txt` |


Next: `04-find-pipes-wildcards.md`
