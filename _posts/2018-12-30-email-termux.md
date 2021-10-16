---
title: Teniendo contraseñas de correos comprometidos con termux
date: 2018-12-30
categories: [Pentesting, Herramientas]
excerpt: Jugando con termux
tags: [termux, OSINT]
---

Bienvenidos a otro blog mio. Hoy buscaremos contraseñas de cuentas comprometida con la herramienta pwnedOrNot en pocas palabras lo que hace esta herramienta es que comprueba si el correo no ha sido comprometido en una violación de datos
 
### Instalación
----

```bash 
chmod +x install.sh
./install.sh
```

Cuando tengamos ya todo instalado procedemos a la instalación de la herramienta
 
### Instalamos la herramienta
----

```bash
git clone https://github.com/thewhiteh4t/pwnedOrNot.git
```  

Entramos a la carpeta o directorio

```bash
cd pwnedOrNot/
```

Ahora ejecutamos la herramienta

```bash
python3 pwnedornot.py -h
```

![termux](/assets/img/post/08/termux.jpg) 