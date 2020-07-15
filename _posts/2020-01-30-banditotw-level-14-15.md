---
layout: default
title: "Level 14-15"
tags: banditoverthewire
---

# Level 14 to 15

## Level Goal
> The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Comments
This was a pretty useful level, it taught be about the 'nc' command, and more importantly a little more on how ssh works and how to submit data to it.

Code Used
------
```bash
nc localhost 30000
*bandit14 password*
```
