---
layout: default
title: "18-19"
tags: banditoverthewire
---

# Level 18 to 19

## Level Goal
> The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

## Comments
On the outside, this does look like it would be complicated, since we weren't able to log into the SSH traditionally. However, it was actually very simple because along with our normal ssh login command, we can also add extra commands to execute after the ssh command. So, we just append 'cat readme' onto the end and therefore, before we get logged out we read the file and get the password.

Code Used
------
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```
