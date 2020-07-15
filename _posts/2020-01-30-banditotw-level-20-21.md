---
layout: default
title: "20-21"
tags: banditoverthewire
---

# Level 20 to 21

## Level Goal
> There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21). NOTE: Try connecting to your own network daemon to see if it works as you think

## Comments
This level took a lot of trial and error as well as research. I did learn a lot about opening listener ports (in the background as processes), scanning them, sending data to them etc.

Code Used
------
```bash
ls
echo "(bandit20 password)" | nc -l localhost -p 56789 &
./suconnect 56789
```
