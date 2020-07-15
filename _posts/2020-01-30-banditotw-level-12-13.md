---
layout: default
title: "Level 12-13"
tags: banditoverthewire
---

# Level 12 to 13

## Level Goal
> The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Comments
This level was definately the most tedious so far, but I am glad that I did it. It taught me a lot about new common compression methods such as 'gzip', and 'bzip2', as well as how to decompress them in the command line.

Code Used
------
```bash
ls
mkdir /tmp/poodle123
xxd -r data.txt > /tmp/poodle123/data.txt
cd /tmp/poodle123
ls
file data.txt
zcat data.txt > zcatted
file zcatted
bzip2 -d zcatted
file zcatted.out
zcat zcatted.out > zcatted_1
file zcatted_1
tar -xvf zcatted_1
file data5.bin
tar -xvf data5.bin
file data6.bin
bzip2 -d data6.bin
file data6.bin.out
tar -xvf data6.bin.out
file data8.bin
zcat data8.bin > zcatted_2
file zcatted_2
zcat data8.bin > zcatted_2
```
