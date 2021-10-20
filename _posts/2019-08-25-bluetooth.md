---
title: Bluetooth Mac Address Spoofing
date: 2019-08-25
categories: [Pentesting, Spoofing]
excerpt: Spoofing Bluetooth
tags: [Spoofing]
---

Hoy les traigo otra técnica de Spoofing y aprenderemos a sumplatar una conexión Bluetooth como en la Serie de Mr. Robot, antes de explicar que hicieron en la serie te encuentra que de aquí en adelante estará de spoiler y vale la pena verse la serie! Así que ve a verla y regresa a ver el procedimiento de este ataque. 

En Mr Robot Elliot aprovecha el sistema Bluetooth del coche del policía para tener acceso a su teclado y así poder controlar el pc.

### Comencemos.
----

Primero que todo debemos iniciar nuestra interfaz de Bluetooth de la siguiente manera: 

```
service bluetooth start
hciconfig hci0 up 
hciconfig hci0 
```

Después debemos obtener todos los dispositivos que estén cerca de nosotros o de cierto rango, para tener sus ips y macs. 

```
btscanner
```

Luego seleccionamos "i" para hacer un escaneo de consulta y así tener los nombres y macs (Están censuradas por motivos de que estos son dispositivos reales.) ahora de hacer spoofing! Solo tenemos que usar la herramienta Spooftooph. Para los que no sepan de que va esta herramienta: «Spooftooph está diseñado para automatizar el proceso de spoofing o clonar información de dispositivos Bluetooth. Hace que un dispositivo Bluetooth esté oculto en un lugar.**»** [Ver mas..](https://kali-linux.net/article/spooftooph/)   
  
También podemos usar la misma herramienta para hacer un escaneo de nuestra área local usando los siguientes parámetros:  

```
spooftooph -i hci0 -s
```

En fin.. Podemos usar cualquiera con que nos de lo que queremos, ahora sin mas rodeos hagamos el spoofing  

```
spooftooph -i hci0 -a MAC -a standby
```

Este comando lo que ara es falsificarse a si misma (hci0) como el nombre (Standby) y mac (AE:06...) del dispositivo.