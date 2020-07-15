---
layout: default
title: "19-20"
tags: banditoverthewire
---

# Level 19 to 20

## Level Goal
> To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

## Comments
I enjoyed this level a lot, I find the concept of executing files on behalf of other users quite interesting, I would like to know more about how this works!

Code Used
------
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```
