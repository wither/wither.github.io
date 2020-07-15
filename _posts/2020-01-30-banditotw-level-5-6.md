---
layout: default
title: "Level 5-6"
tags: banditoverthewire
---

# Level 5 to 6

## Level Goal
> The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: ~ human-readable ~ 1033 bytes in size ~ not executable

## Comments
This level was basically an extension of the previous level. All I had to do was add a size parameter using '-size' with a value of 1033 bytes (1033c). From this, I could almost guarantee that the file that I find successfully would be the file containing the flag simply due to the low chance of more than one file being exactly 1033 bytes in size.

Code Used
------
```bash
ls
cd inhere
find . -size 1033c -exec file {} + | grep -w text
cat ./maybehere07/.file2
```
