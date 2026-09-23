# Mr. Robot

Esta máquina virtual tiene tres claves ocultas en diferentes ubicaciones. Tu objetivo es encontrar las tres. Cada clave es progresivamente más difícil de encontrar.

La máquina virtual no es demasiado complicada. No hay ninguna explotación avanzada ni ingeniería inversa. El nivel se considera de principiante a intermedio.

Descarga [aquí](https://www.vulnhub.com/entry/mr-robot-1,151/)

## Resolución

## Flag 1: enumeración

Como suele ser habitual, comenzamos con un escaneo de puertos para comprobar que servicios y versiones hay disponibles en esta máquina. En este caso nos encontramos con un servidor apache en el puerto 80 y 443. Si profundizamos un poco más 

```console
root@ine# nmap -sS -p- -T4 -sC -sV target.ine.local
root@ine# nmap -p80,443 --script http-enum target.ine.local
```

![nmap](img/nmap.png)

Si profundizamos un poco más en la enumwp-eración, podemos encontrar algunos directorios típicos que nos confirman que nos enfrentamos a una web creada con wordpress.

```console
root@ine# nmap -p80,443 --script http-enum target.ine.local
```

![nmap2](img/nmap2.png)

Vemos que el archivo `robots.txt` está disponible. Este documento incluye directorios web que no queremos que indexen los navegadores. Revisamos su contenido y encontramos la primera flag, además de un diccionario con palabras que podremos usar más adelante.

![flag1](img/flag1.png)

## Flag 2: Explotación wordpress y obtención de usuarios locales

Para obtener acceso a la aplicación wordpress encontramos al menos dos formas. Aquí se explica la que tiene más relación con las técnicas necesarias para la certificación eJPT. Una de las técnicas más comunes en esta certificación es el uso de la fuerza bruta y en este caso podemos usar hydra para tratar de conseguir tanto el usuario como sus credenciales.

El método `http-post-form` de hydra necesita al menos tres parámetros: usuario, contraseña y mensaje de error. Aún no disponemos de un usuario, por lo que probar todas las palabras del diccionario que hemos encontrado antes puede tardar demasiado. La solución a esto pasa por el tercer parámetro. Si hacemos un intento de iniciar sesión para que la aplicación muestre el mensaje de error nos encontramos con *"Invalid username"*. Esto nos ofrece mucha información y la posibilidad de enumerar usuarios.

![login](img/login.png)

Para enumerar los usuarios necesitamos los valores de los campos del formulario. Usamos burpsuite y foxyproxy para interceptar un intento de inicio de sesión.

![burp](img/burp.png)

Una vez que conocemos estos parámetros, usamos hydra y la lista obtenida durante la fase de reconocimiento inicial.

```console
kali@kali$ hydra -L fsocity.dic -p test 192.168.1.142 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^:Invalid username"
```

![hydra1](img/hydra1.png)

Si ahora intentamos iniciar sesión con el usuario `Elliot`, vemos que el mensaje cambia.

![login2](img/login2.png)
