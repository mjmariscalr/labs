# Informe de Evaluación de Seguridad
#### Enumeration CTF 1 – eJPT Lab

---

## 1. Resumen

Tercer laboratorio del curso de preparación para la certificación eJPT de INE. Se centra en técnicas de enumeración de servidores. En este laboratorio nos vamos a encontrar con distintos servicios como: SSH, SMB o FTP.

### Resultados generales

- Flags obtenidas: 4/4
- Tipo de hallazgos:  Information disclosure / Misconfiguration / Debilidad de credenciales
- Dificultad: **Media**

## 2. Alcance y Metodología

### Alcance

- Objetivo: `IP`
- Tipo de evaluación: Black-box
- Sin credenciales proporcionadas
- Entorno de laboratorio controlado

### Metodología aplicada

El análisis se realizó combinando técnicas de:

- Enumeración de servicios
- Fuerza bruta sobre credenciales

### Flags

- Flag 1: Hay un recurso compartido Samba que permite acceso anónimo. ¡A ver qué hay dentro!
- Flag 2: Uno de los usuarios de Samba tiene una contraseña débil. Su recurso privado, que tiene el mismo nombre que su usuario, está en riesgo.
- Flag 3: Sigue la pista proporcionada en la flag anterior para descubrir esta.
- Flag 4: Este es un aviso destinado a disuadir a usuarios no autorizados de iniciar sesión.

### Herramientas utilizadas

- Nmap
- Metasploit
- Hydra
- enum4linux
- smbclient
- smbmap

## 3. Hallazgos

### Titulo

descripcion

#### Impacto

Ejemplo:
Aunque no es una vulnerabilidad directa, puede facilitar:
- Enumeración de endpoints ocultos
- Reducción del tiempo de reconocimiento para un atacante

#### Recomendación
Ejemplo:
- Evitar incluir rutas sensibles en `robots.txt`
- Asumir acceso público a este archivo

#### Resolución

Explicar paso a paso las acciones realizadas para resolver esta parte, con todos los comandos listos para copiar de forma que sea reproducible

## 4. Conclusiones

Comentar lo aprendido

- 
