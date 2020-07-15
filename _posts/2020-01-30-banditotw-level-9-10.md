---
layout: default
title: "9-10"
tags: banditoverthewire
---

# Level 9 to 10

## Level Goal
> The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.

## Comments
This level was quite simple in that it was only a matter of searching for the right thing in the file. For this, I used 'strings' instead of 'cat' to read the file, and 'grep' it for any '=' that was in it. And sure enough, from this, I found the flag.

Code Used
------
```bash
ls
strings data.txt | grep '===='
```
