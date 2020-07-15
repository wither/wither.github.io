---
layout: default
title: "16-17"
tags: banditoverthewire
---

# Level 16 to 17

## Level Goal
> The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

## Comments
Just like the other harder levels, this actually taught me a lot of useful skills that I learned the hard way. Some things I used for this level include things like scanning open ports with 'nmap', creating and editing files using 'vim', 'openssl', file permissions using 'chmod' and more. I really enjoyed this level because it has several steps and forced me to think on my feet and outside of the box. For example, when I first created the 'sshkey.private' it wouldn't allow me to use it due to the file being too open (i.e bad file permissions), so I had to change the permissions of the file to 400 so that I was able to use it when using SSL.

Code Used
------
```bash
nmap localhost -p 31000-32000
openssl s_client -connect localhost:31790
*bandit16 password*
mkdir -v /tmp/notansshkey
cd /tmp/notansshkey
vi sshkey.private
ssh -i sshkey.private bandit17@localhost
chmod 400 sshkey.private
ssh -i sshkey.private bandit17@localhost
```
