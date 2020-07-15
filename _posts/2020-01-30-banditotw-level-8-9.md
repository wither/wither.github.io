---
layout: default
title: "Level 8-9"
tags: banditoverthewire
---

# Level 8 to 9

## Level Goal
> The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## Comments
For this level, I had a knew what I had to do to find the flag, but was not sure exactly how to get there. I knew that the data had to be sorted, and then filtered into only unique entries but up until this point I had not came across the tools to do just that. So, after doing some research, I came to exactly this. I found that 'sort' and 'uniq' were exactly he commands I was searching for for this level.

Code Used
------
```bash
ls
sort data.txt | uniq -u
```
