---
layout: default
title: "Level 6-7"
tags: banditoverthewire
---

# Level 6 to 7

## Level Goal
> The password for the next level is stored somewhere on the server and has all of the following properties: ~ owned by user bandit7 ~ owned by group bandit6 ~ 33 bytes in size

## Comments
This level was very similar to the previous two levels. I used the same command pattern but slightly altered it to meet the requirements of the goal. I searched the entire server instead of the current directory using 'find /' instead of 'find .', and also added '-user' and '-group' parameters.

Code Used
------
```bash
find / -size 33c -user bandit7 -group bandit6
cat /var/lib/dpkg/info/bandit7.password
```
