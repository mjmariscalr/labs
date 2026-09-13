# Web Application Penetration Testing CTF 1

## Flag 1: Sometimes, important files are hidden in plain sight. Check the root ('/') directory for a file named 'flag.txt' that might hold the key to the first flag.

La aplicación web dispone de un lector de archivos locales. Si seleccionamos uno de ellos, vemos que se busca el archivo mediante una consulta, probablemente php.

![file](img/file)
![file1](img/file1)

Cambiamos el nombre del archivo el la url por `/flag.txt` para mostrar el contenido de la primera.

## Flag 2: Explore the structure of the server's directories. Enumeration might reveal hidden treasures.



## Flag 3: The login form seems a bit weak. Trying out different combinations might just reveal the next flag.



## Flag 4: The login form behaves oddly with unexpected inputs. Think of injection techniques to access the 'admin'


