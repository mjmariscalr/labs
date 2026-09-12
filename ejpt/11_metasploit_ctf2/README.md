# Host & Network Penetration Testing: The Metasploit Framework CTF 2

## Flag 1: Enumerate the open port using Metasploit, and inspect the RSYNC banner closely; it might reveal something interesting.

Para obtener esta flag, primero debemos conseguir acceso al objetivo. El primer paso es enumerar los posibles vectores de ataque.

```console
root@ine# nmap -sS -p- -T4 -sC -sV target.ine.local
```

![nmap](img/nmap.png)

## Flag 2: The files on the RSYNC server hold valuable information. Explore the contents to find the flag.



## Flag 3: Try exploiting the webapp to gain a shell using Metasploit on target2.ine.local.



## Flag 4: Automated tasks can sometimes leave clues. Investigate scheduled jobs or running processes to uncover the hidden flag.


