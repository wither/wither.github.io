---
layout: default
title: "Level 0-1"
tags: banditoverthewire
---

# Level 0 → 1

## Level Goal
> The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Comments
This was quite an easy level as expected, all I needed to do here was connect to the Bandit servers via SSH on the port 2220 and then locate the "readme" file in the home directory, read it and then use the password located inside of it to access level 1.

Code Used
------
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0
ls
cat readme
```
