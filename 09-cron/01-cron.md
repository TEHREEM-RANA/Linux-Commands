# 09-01 Cron Jobs: Run Things Automatically

`cron` is a background service that runs scheduled tasks. A scheduled task is a **cron job**.

## Check cron is running

```bash
systemctl status cron
```
You want `Active: active (running)`. If not:

```bash
sudo systemctl start cron
sudo systemctl enable cron
```
`enable` makes it start at boot.

## crontab

```bash
crontab -l
```
What it does: lists your cron jobs. (`no crontab for tehreem` means none yet.)

```bash
crontab -e
```
What it does: opens your crontab to edit.

```bash
crontab -r
```
What it does: removes your **entire** crontab. Do not use it casually.

```bash
sudo crontab -e
```
What it does: edits root's crontab. Root jobs run with root rights, so be careful.

## The five fields

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week  (0-7)
│ │ │ └──── Month        (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour         (0-23)
└────────── Minute       (0-59)
```
`*` means every value.

## Common schedules

| Schedule | Meaning |
|---|---|
| `*/5 * * * * cmd` | Every 5 minutes |
| `0 * * * * cmd` | Every hour at minute 0 |
| `30 2 * * * cmd` | Every day at 02:30 |
| `0 3 * * 0 cmd` | Every Sunday at 3:00 AM |
| `0 0 1 * * cmd` | Midnight on the 1st of every month |
| `0 9 * * 1,3,5 cmd` | 9:00 AM Monday, Wednesday, Friday |
| `0 9 * * 1-5 cmd` | 9:00 AM Monday to Friday |

Day of week: `0` or `7` = Sunday, `1` = Monday ... `6` = Saturday.

Symbols: `*` every, `*/5` every 5, `1,5,10` specific values, `1-5` range.

## Use a script and full paths

```bash
nano /home/tehreem/backup.sh
```
```bash
#!/bin/bash
tar -czf /home/tehreem/backup.tar.gz /home/tehreem/project
```
```bash
chmod +x /home/tehreem/backup.sh
```
Crontab line:

```text
0 2 * * * /home/tehreem/backup.sh
```
Runs every day at 2 AM.

Cron does not have your normal terminal environment. Use full paths (`/home/tehreem/backup.sh`, `/usr/bin/tar`). Find a full path with `which tar` or `command -v tar`.

## Save the output to a log

```text
* * * * * /home/tehreem/test.sh >> /home/tehreem/cron.log 2>&1
```
- `>>` adds normal output to the log
- `2>&1` sends errors to the same place

## First test

```text
*/5 * * * * echo "Cron works!" >> /home/tehreem/cron.log
```
Wait a few minutes, then:

```bash
cat /home/tehreem/cron.log
```
If the line repeats, cron works.

## If it did not run

```bash
crontab -l
tail /home/tehreem/cron.log
systemctl status cron
```
Cron uses the server's timezone. Check it when you schedule jobs.


Next: `../10-filesystem/01-directory-tree.md`
