---
title: Robando Informacion de servidores y de cualquier dispositivos con SHODAN/FTP
date: 2018-12-30
categories: [Pentesting, Protocolos]
excerpt: Jugando con FTP
tags: [FTP, Shodan, Protocolos]
---

Usaremos shodan para acceder a dispositivos de almacenamiento en la red, esto se puede hacer en cualquier terminal en el que se pueda usar ftp ¿Que es FTP? se preguntara los que no saben bueno ftp es un protocolo de trasferencia de ficheros o archivos entre sistemas conectados a una red TCP y que este basada en la arquitectua cliente-servidor. Bueno con esto podemos conectarnos remotamente a un servidor lo cual podremos descargar, ver, editar, o robar los archivos y ya que FTP su seguridad es muy "kk", pero lo bueno es que su conexión es muy rápida. Usaremos SHODAN aquí aprovechando esto para robar información de dispositivos o USBs.

También se puede usar en terminales de android como termux, userland o si tienes windows esta cmd! tambien se puede hacer manualmente o desde un programa. si queires conectarte aun servidor FTP

Nosotros lo haremos más pro, desde una web para conectarnos al servidor, jaja. Mucha cosa si lo podemos hacer desde nuestro navegador, pero recomiendo tener prevenciones al descargar, ver o editar algo si lo harás en una web.

 ![seagate](/assets/img/post/12/seagate.jpg)

### Seagate dato interesante:

Seagate según wikipedia: Seagate Technology (NYSE: STX) es un importante fabricante estadounidense de discos duros, fundado en 1979 y con sede en Scotts Valley, California. La compañía está registrada en las Islas Caimán. Sus discos duros son usados en una variedad de computadoras, desde servidores, equipos de escritorio y portátiles hasta otros dispositivos de consumo como PVRs, la consola Xbox de Microsoft y la línea Creative Zen de reproductores de audio digital.

Ya sabiendo esto seagate vende muchas cosas a sus clientes como hardware cual recolecta nuestra información fotos, pass, documentos, etc, etc. Y lo bueno de esto es que estos datos "privados" es que están en la nube para que nosotros podremos obtenerlo accediendo desde el puerto 21 desde shodan:

Ponemos en shodan: `port:21 Seagate` Central Shared IP que usare `91.88.49.158`

  

### Configuración y web:
---
![shodan](/assets/img/post/12/shodan.jpg)
![ftp1](/assets/img/post/12/ftp1.jpg)
![ftp2](/assets/img/post/12/ftp2.jpg)
![ftp3](/assets/img/post/12/ftp3.jpg)

Este otro para tener más información de dispositivos o servidores ewe

```bash
port:21 214-ADMIN_LOGIN IP que usare 79.19.19.122
```

![shodan2](/assets/img/post/12/shodan.jpg)
![ftp4](/assets/img/post/12/ftp1.jpg)
![ftp5](/assets/img/post/12/ftp2.jpg)

Hasta aquí terminaríamos una parte de shodan si veo que tiene mucho apoyo hago un blog de explotar puertos FTP o lo que quieran en comentarios. `^^)7`

[**Net2ftp**](https://www.net2ftp.com/index.php)
