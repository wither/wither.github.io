---
layout: default
title: "Level 13-14"
tags: banditoverthewire
---

# Level 13 to 14

## Level Goal
> The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

## Comments
This was level was pretty straight forward. I simply had to connect to the bandit14 ssh on my localhost, using the '-i' command to use the sshkey as a password.

Code Used
------
```bash
ssh -i sshkey.private bandit14@localhost
```
