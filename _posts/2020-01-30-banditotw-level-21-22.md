---
layout: default
title: "21-22"
tags: banditoverthewire
---

# Level 21 to 22

## Level Goal
> A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Comments
Very simple. all I had to do was read the contents of the bandit22 cronjob file, which displayed a list of commands, one of them containing the directory '/usr/bin/cronjob_bandit22.sh'. I found this interesting, so I then decided to read the contents of this file instead. This file contained a list of commands, one of which was a chmod command running on a file. So, I then read the contents of that file which gave me the password.

Code Used
------
```bash
ls
cd /etc/cron.d/
cat /etc/cron.d/cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
