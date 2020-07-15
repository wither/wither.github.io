---
layout: default
title: "Level 4-5"
tags: banditoverthewire
---

# Level 4 to 5

## Level Goal
> The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

## Comments
This level was admittedly harder than all previous levels. For this, I was forced to research about commands like 'find', 'file' and 'grep', as well as the concept of 'piping' commands using '|' (a pipe). To complete the task and find a "human-readable" file, I knew I had to find a file that contained text. So, with the end result, I searched all files, executed the file command on them and grepped them for text.

Code Used
------
```bash
ls
cd inhere
find . -exec file {} + | grep -w text
cat ./-file07
```
