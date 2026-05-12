# Informe de Evaluación de Seguridad
#### Footprinting and scanning CTF 1 – eJPT Lab

---

## 1. Resumen

El reconocimiento implica recopilar datos de forma activa o pasiva, como encabezados del servidor, puertos abiertos, directorios expuestos y configuraciones del sistema. Técnicas como el escaneo, la consulta de registros DNS, el examen de archivos de aplicaciones web (por ejemplo, robots.txt) y el análisis de encabezados de respuesta ayudan a descubrir información crítica que puede ser útil en fases posteriores de explotación. Un reconocimiento efectivo permite a los evaluadores mapear la superficie de ataque, priorizar objetivos y planificar su enfoque con una detección mínima por parte de las defensas del sistema.

### Resultados generales

- Flags obtenidas: 4/4
- Tipo de hallazgos: Divulgación de información - Errores de configuración
- Dificultad: **Baja**

## 2. Alcance y Metodología

### Alcance

- Objetivo: `target.ine.local`
- Tipo de evaluación: Black-box
- Sin credenciales proporcionadas
- Entorno de laboratorio controlado

### Metodología aplicada

El análisis se realizó combinando técnicas de enumeración activa:

- Escaneo de puertos
- Enumeración de servicios

### Flags

- **Flag 1:** El servidor anuncia con orgullo su identidad en cada respuesta. Mira con atención; podrías encontrar algo inusual.
- **Flag 2:** Las instrucciones del guardián suelen revelar lo que debería permanecer oculto. No olvides leer entre líneas.
- **Flag 3:** El acceso anónimo a veces conduce a tesoros olvidados. Conéctate y explora el directorio; podrías encontrar algo valioso.
- **Flag 4:** Una base de datos con un nombre apropiado puede ser bastante reveladora. Revisa las configuraciones para descubrir el tesoro oculto.

### Herramientas utilizadas

- Nmap
- FTP
- MySQL

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
