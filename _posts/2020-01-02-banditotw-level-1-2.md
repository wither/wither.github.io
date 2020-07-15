---
layout: default
title: "Level 1-2"
tags: banditoverthewire
---

# Level 1 -> 2

## Level Goal
> The password for the next level is stored in a file called - located in the home directory

## Comments
For this level, I could not simply do "cat - " as ’-‘ means reading from/to stdin in a shell. So, I had to find a way around it by defining the path to the text-file, so that it could not be mistaken for a command.

Code Used
------
```bash
ls
cat ./-
```
