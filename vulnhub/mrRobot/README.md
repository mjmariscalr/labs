# Mr. Robot

Esta máquina virtual tiene tres claves ocultas en diferentes ubicaciones. Tu objetivo es encontrar las tres. Cada clave es progresivamente más difícil de encontrar.

La máquina virtual no es demasiado complicada. No hay ninguna explotación avanzada ni ingeniería inversa. El nivel se considera de principiante a intermedio.

Descarga [aquí](https://www.vulnhub.com/entry/mr-robot-1,151/)

## Resolución

Como suele ser habitual, comenzamos con un escaneo de puertos para comprobar que servicios y versiones hay disponibles en esta máquina. En este caso nos encontramos con un servidor apache en el puerto 80 y 443. Si profundizamos un poco más 

```console
root@ine# nmap -sS -p- -T4 -sC -sV target.ine.local
root@ine# nmap -p80,443 --script http-enum target.ine.local
```

![nmap](img/nmap.png)

Si profundizamos un poco más en la enumeración, podemos encontrar algunos directorios típicos que nos confirman que nos enfrentamos a una web creada con wordpress.

```console
root@ine# nmap -p80,443 --script http-enum target.ine.local
```

![nmap2](img/nmap2.png)

Vemos que el archivo `robots.txt` está disponible. Este documento incluye directorios web que no queremos que indexen los navegadores. Revisamos su contenido y encontramos la primera flag, además de un diccionario con palabras que podremos usar más adelante.

![flag1](img/flag1.png)

