# 07-01 Environment Variables, PATH and .bashrc

An environment variable is a named value in the shell. Programs can read it.

## See and use variables

```bash
echo $HOME
echo $USER
echo $SHELL
```
What it does: prints the value. `$` means "give me the value". Without `$`, `echo HOME` prints the word `HOME`.

```bash
printenv
env
```
What it does: shows all environment variables.

Example values: `USER=tehreem`, `HOME=/home/tehreem`, `SHELL=/bin/bash`.

## Create your own

```bash
name="Tehreem"
echo $name
```
No spaces around `=`.

- Right: `name="Tehreem"`
- Wrong: `name = "Tehreem"`

## Shell variable vs environment variable

```bash
name="Tehreem"
```
A shell variable. Programs you start do **not** receive it.

```bash
export APP_ENV="production"
```
`export` passes it to programs started from this shell (child processes).

Common names: `DATABASE_URL`, `API_KEY`, `PORT`, `APP_ENV`, `DEBUG`.
Environment variables are not a safe secret store. They can leak through logs or process inspection.

## PATH — where commands are found

```bash
echo $PATH
```
Example: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`

Folders are separated by `:`. When you type `ls`, the shell searches these folders until it finds `ls`.

## Where does a command come from?

```bash
which ls
command -v ls
type ls
type cd
```
- `which` and `command -v` show the location.
- `type` also shows aliases, functions and built-ins. `type cd` says `cd` is a shell builtin.

## Why `./script.sh`?

The current folder `.` is usually **not** in PATH. So `hello.sh` gives `command not found`, but `./hello.sh` works. This is also a safety feature.

## Add a folder to PATH

```bash
export PATH="$PATH:/home/tehreem/scripts"
```
What it does: takes your existing PATH and adds one folder at the end.

Never do `export PATH="/home/tehreem/scripts"` alone. That **replaces** PATH, and `ls`, `cat`, `sudo` may stop working.

## Temporary vs permanent

- `export` in the terminal lasts only for this session.
- For permanent settings, add the line to `~/.bashrc`:

```bash
export APP_ENV=production
export PATH="$PATH:$HOME/scripts"
```

Load it now:

```bash
source ~/.bashrc
```
What it does: runs the file in the current shell. Short form: `. ~/.bashrc`

## Worked example

```bash
echo $PATH
mkdir -p ~/scripts
nano ~/scripts/hello
```
Put this in the file:

```bash
#!/bin/bash
echo "Hello from my script!"
```
Then:

```bash
chmod +x ~/scripts/hello
hello                       # fails: not in PATH
~/scripts/hello             # works
export PATH="$PATH:$HOME/scripts"
hello                       # works now
command -v hello
```


Next: `../08-archives/01-tar-gzip-zip.md`
