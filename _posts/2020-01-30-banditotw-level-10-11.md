---
layout: default
title: "Level 10-11"
tags: banditoverthewire
---

# Level 10 to 11

## Level Goal
> The password for the next level is stored in the file data.txt, which contains base64 encoded data

## Comments
This was simply decoding the file using the 'base64 -d' command.

Code Used
------
```bash
ls
base64 -d data.txt
```
