# Host & Network Penetration Testing: Post-Exploitation CTF 1

## Flag 1: The file that stores user account details is worth a closer look. (target1.ine.local)

Para obtener esta flag, primero debemos conseguir acceso al objetivo. El primer paso es enumerar los posibles vectores de ataque.

```console
root@ine# nmap -sS -p- -T4 -sC -sV target.ine.local
```

![nmap1](img/nmap1.png)

Nos encontramos abierto el puerto 22 funcionando sobre `libssh 0.8.3`, que como ya sabemos es vulnerable y podemos usar el módulo `auxiliary/scanner/ssh/libssh_auth_bypass` para explotarlo.

![exploit](img/exploit.png)

Usamos la sesión creada para ver el contenido de `/etc/passwd` y encontrar la primera flag.

![flag1](img/flag1.png)

## Flag 2: User groups might reveal more than you expect.

Para esta flag solo es necesario mostrar el contenido de `/etc/group`

![flag2](img/flag2.png)

## Flag 3: Scheduled tasks often have telling names. Investigate the cron jobs to uncover the secret.



## Flag 4: DNS configurations might point you in the right direction. Also, explore the home directories for stored credentials.



## Flag 5: Use the discovered credentials to gain higher privileges and explore the root's home directory on target2.ine.local.
