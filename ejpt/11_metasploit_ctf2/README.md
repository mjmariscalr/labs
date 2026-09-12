# Host & Network Penetration Testing: The Metasploit Framework CTF 2

## Flag 1: Enumerate the open port using Metasploit, and inspect the RSYNC banner closely; it might reveal something interesting.

Enumerando los servicios disponibles con nmap encontramos `rsync`. `rsync` es una herramienta para sincronizar y copiar archivos y directorios, normalmente entre dos máquinas o entre dos ubicaciones del mismo equipo. Cuando se habla de rsync como servicio, se refiere a ejecutar rsync en modo daemon, es decir, como un proceso que queda escuchando conexiones de otros equipos. Para copias entre servidores, rsync sobre SSH suele ser la opción más sencilla y segura.

```console
root@ine# nmap -sS -p- -T4 -sC -sV target1.ine.local
```

![nmap](img/nmap.png)

Nos conectamos al servicio para obtener información y nos encontramos la primera flag.

```console
root@ine# rsync rsync://target1.ine.local
```

![flag1](img/flag1.png)

## Flag 2: The files on the RSYNC server hold valuable information. Explore the contents to find the flag.



## Flag 3: Try exploiting the webapp to gain a shell using Metasploit on target2.ine.local.



## Flag 4: Automated tasks can sometimes leave clues. Investigate scheduled jobs or running processes to uncover the hidden flag.


