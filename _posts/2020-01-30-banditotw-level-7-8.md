---
layout: default
title: "7-8"
tags: banditoverthewire
---

# Level 7 to 8

## Level Goal
> The password for the next level is stored in the file data.txt next to the word millionth

## Comments
This was was pretty simple. All I had to do was read the file using 'cat' and 'grep' it for the term 'millionth'. This returned 'millionth' followed by the flag.

Code Used
------
```bash
ls
cat data.txt | grep millionth
```
