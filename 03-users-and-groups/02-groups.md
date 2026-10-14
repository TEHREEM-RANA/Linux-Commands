# 03-02 Groups

A group lets you give access to many users at once. Example: group `developers` has Alice, Bob and Charlie. Give the group access to a file once, and all three get it.

A user can be in many groups.

## See groups

```bash
groups tehreem
id tehreem
```

## Create a group and add a user

```bash
sudo groupadd developers
```
What it does: creates the group `developers`.

```bash
sudo usermod -aG developers tehreem
```
What it does: adds `tehreem` to `developers` and keeps his other groups.

- `-a` = append
- `-G` = supplementary groups

After this, log out and log in again to see the new membership.

## Same name for user and group

When you create a user, Linux often creates a group with the same name. In `ls -l` you may see `tehreem tehreem`. First is the owner, second is the group.


Next: `../04-permissions/01-read-permissions.md`
