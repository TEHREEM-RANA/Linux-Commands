# 04-04 umask — Default Permissions for New Files

`umask` removes permission bits from the default when a **new** file or folder is created.
It is a filter. It does not change existing files.

## Commands

```bash
umask
```
What it does: shows the current mask. Example: `0022`

```bash
umask -S
```
What it does: shows the mask in letters.

```bash
umask 027
```
What it does: sets a stricter mask for this shell only.

## How the numbers work

- New **file** starts at `666` (no execute, so a new text file cannot run by accident).
- New **directory** starts at `777` (execute is needed to enter it).

| Item | Base | umask 022 | umask 027 |
|---|---|---|---|
| New file | 666 | 666 - 022 = **644** | **640** |
| New directory | 777 | 777 - 022 = **755** | **750** |

With `umask 077`, new items are visible to the owner only.

(Subtraction is the easy way to explain it. Technically it removes bits, but the answers here are the same.)


Next: `05-fix-permission-errors.md`
