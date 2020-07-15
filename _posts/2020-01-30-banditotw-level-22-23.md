---
layout: default
title: "Level 22-23"
tags: banditoverthewire
---

# Level 22 to 23

## Level Goal
> The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

## Comments
Very similar to the previous level, except now using an MD5 hash.

Code Used
------
```bash
cd /etc/cron.d
ls
cat cronjob_bandit23
cat /usr/bin/cronjob_bandit23.sh
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
cat tmp/8ca319486bfbbc3663ea0fbe81326349
```
