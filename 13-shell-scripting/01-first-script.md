# 13-01 Your First Shell Script

A **shell** reads the commands you type and passes them to the kernel.
A **shell script** is a text file of commands that run line by line. It is used for automation, backups, admin tasks and small tools.

| Shell | Notes |
|---|---|
| `sh` (Bourne Shell) | Traditional, fast, lightweight, basic features |
| `bash` (Bourne Again Shell) | Default on Ubuntu. Best for server and automation scripts |
| `zsh` (Z Shell) | Modern interactive shell: autocorrect, spelling check, autocompletion, customisation |

This course uses **bash**.

## Write a script

```bash
nano hello.sh
```
Put this in the file:

```bash
#!/bin/bash
# my first script
echo "Hello Tehreem"
```

- Line 1 `#!/bin/bash` is the **shebang**. It tells Linux which shell runs the script.
- A line that starts with `#` (after line 1) is a comment.

## Run it (two ways)

```bash
bash hello.sh
```
What it does: runs the script with bash. No permission change needed.

```bash
chmod +x hello.sh
./hello.sh
```
What it does: gives execute permission, then runs the script directly.

If you type `hello.sh` without `./`, you get `command not found`. The current folder is not in PATH. See `../07-environment/01-variables-path-bashrc.md`.

## Check which shell you use

```bash
echo $SHELL
echo $0
```

Next: `02-variables.md`
