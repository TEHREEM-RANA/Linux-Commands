# 03-01 Users

Linux is multi-user. Each user has an account, files and permissions.

## Check current user

```bash
whoami
```
What it does: shows your username.

```bash
id
```
What it does: shows your UID (user ID), GID (group ID) and groups.

## Create a user (Ubuntu)

```bash
sudo adduser guest
```
What it does: creates user `guest`. It asks for a password, full name and optional details. It also creates the home folder `/home/guest`.

## Switch user

```bash
su - guest
```
What it does: switches to `guest`. The `-` starts a login shell: you go to his home folder with his environment.

```bash
whoami
pwd
```
These now show `guest` and `/home/guest`.

```bash
exit
```
What it does: goes back to your previous user.

## Information about a user

```bash
id guest
```
Example: `uid=1001(guest) gid=1001(guest) groups=1001(guest)`

```bash
groups guest
```
Example: `guest : guest sudo`

## Give sudo (admin) rights

```bash
sudo usermod -aG sudo guest
```
What it does: adds `guest` to the `sudo` group. He can then run `sudo command`.

`sudo` does not make the user permanently root. It runs one command with higher rights.

After a group change, the user may need to log out and log in again.

## Change a password

```bash
sudo passwd guest
```

## Delete a user

```bash
sudo userdel guest
```
What it does: removes the account only.

```bash
sudo userdel -r guest
```
What it does: removes the account **and** the home folder. This is permanent.

## What does `usermod -aG sudo guest` mean?

| Part | Meaning |
|---|---|
| `sudo` | Run as administrator |
| `usermod` | Modify a user |
| `-G` | Set supplementary groups |
| `-a` | Append (keep old groups) |
| `sudo` (second) | The group to add |
| `guest` | The user to change |

Why `-a` matters: `-G` alone can **replace** Guest's other groups. `-aG` **adds** one group and keeps the rest.


Next: `02-groups.md`
