# Web Application Penetration Testing CTF 1

## Flag 1: Sometimes, important files are hidden in plain sight. Check the root ('/') directory for a file named 'flag.txt' that might hold the key to the first flag.

La aplicación web dispone de un lector de archivos locales. Si seleccionamos uno de ellos, vemos que se busca el archivo mediante una consulta, probablemente php.

![file](img/file)
![file1](img/file1)

Cambiamos el nombre del archivo el la url por `/flag.txt` para mostrar el contenido de la primera.

![flag1](img/flag1)

## Flag 2: Explore the structure of the server's directories. Enumeration might reveal hidden treasures.

Enumeramos los directorios y encontramos 4. 

```console
root@ine# dirb http://target.ine.local /usr/share/wordlists/dirb/common.txt
```

![dirb](img/dirb)

Por la naturaleza de los laboratorios y el nombre de los directorios, sabemos que lo más probable es que la flag se encuentre en `secured`. Al tratarse de pocos directorios podemos enumerar de forma manual, accediendo al directorio mediante el navegador o usando curl para obtener la flag.

```console
root@ine# curl http://target.ine.local/secured/flag.txt
```

![flag2](img/flag2)

## Flag 3: The login form seems a bit weak. Trying out different combinations might just reveal the next flag.

Para esta flag podemos realizar un ataque de fuerza bruta contra el login de la web. Para ello usamos el servicio `http-post-form` en hydra, que necesita conocer el nombre de los campos a atacar, en este caso: usuario y contraseña. Al tratarse de un formulario html, podemos conocer los nombre viendo el código fuente de la página desde el navegador.

![fuente](img/fuente)

```console
root@ine# hydra -L /usr/share/seclists/Usernames/top-usernames-shortlist.txt -P Desktop/wordlists/100-common-passwords.txt target.ine.local http-post-form "/login:username=^USER^&password=^PASS^:F=Invalid username or password"
```

![hydra](img/hydra)

Iniciamos sesión con el usuario guest y obtenemos la flag

![flag3](img/flag3)

## Flag 4: The login form behaves oddly with unexpected inputs. Think of injection techniques to access the 'admin'

Esta flag se trata de una inyección de código sql en el formulario. Hay varios formatos que pueden funcionar, pero yo he usado `' OR '1'='1`

![flag4](img/flag4)
