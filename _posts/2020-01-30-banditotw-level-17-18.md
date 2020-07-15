---
layout: default
title: "17-18"
tags: banditoverthewire
---

# Level 17 to 18

## Level Goal
> There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

## Comments
This was a pretty simple level, all I had to do was use the 'diff' command to find the difference between the two files. The newest version of the line had to be the flag.

Code Used
------
```bash
ls
diff passwords.old passwords.new
```
