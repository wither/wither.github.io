---
layout: default
title: "11-12"
tags: banditoverthewire
---

# Level 11 to 12

## Level Goal
> The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Comments
For this one, I knew it was rot13 but I wasn't quite sure how to decode it in the command line. So, after a quick google search I found that 'tr' was exactly what I was looking for.

Code Used
------
```bash
ls
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
