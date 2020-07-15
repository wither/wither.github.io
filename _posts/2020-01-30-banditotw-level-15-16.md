---
layout: default
title: "Level 15-16"
tags: banditoverthewire
---

# Level 15 to 16

## Level Goal
> The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption. Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

## Comments
Good level, taught me a bit about SSL connection and some useful opensel and s_client stuff.

Code Used
------
```bash
openssl s_client -connect localhost:30001
(bandit15 password)
```
