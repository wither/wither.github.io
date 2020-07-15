---
layout: default
title: "Level 2-3"
tags: banditoverthewire
---

# Level 2 to 3

## Level Goal
> The password for the next level is stored in a file called 'spaces in this filename' located in the home directory.

## Comments
I had to treat the file name as a string so that spaces would not be considered as part of the file path. I also could've also used '\' to escape the spaces.

Code Used
------
```bash
ls
cat "spaces in this filename"
```
