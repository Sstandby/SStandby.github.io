---
title: hackeando una cuenta de WhatsApp QRJacking
date: 2018-12-30
categories: [Pentesting, Herramientas]
excerpt: Aprendiendo QRJacking
tags: [WhatsApp]
---

![qrws](/assets/img/post/10/qrwasa.jpg) 
 
Esta es una de mis favoritas maneras al momento de acceder a una cuenta de WhatsApp a este método se conoce como QRLJacking que hasta ahora supe de el y ya pude lograrlo manualmente, y automáticamente con una herramienta que les mostrare. 

Estaba pensando en un nuevo reto de estenografía para la comunidad para ayudarle a tazz un poco y se me ocurrió la gran idea de hacerlo con un código QR ¿Que te hace recordar? ¡Pues claro! Al código QR de WhatsApp teóricamente acerté de que se podría utilizar para hackear una cuenta solo debemos hacer cargar el archivo qrHandler.php en nuestro servidor ya después este archivo php hará el código QR de base64 en un archivo.jpg valido y para utilizar después utilizaremos el archivo HTML para implementar esa imagen en un phishing para hacer que la víctima caiga para escanear el código QR, pero no creas que ya se acabó.

  
Después que tengamos esas dos cosas listas vamos a nuestro navegador Firefox en el buscador escribimos "about:config" después haremos clic en el botón de "Tendré cuidado, lo prometo" después tendremos que buscar "security.cps.enable" y cambiar el valor a "false"


Ahora instalamos Greasemokey y tener el archivo cargado y en ejecución que sería "WhatsAppQRJackingModule.js" después vamos a [whatsapp](https://web.whatsapp.com/) esperando que se cargue una sesion ¡Ahora si! Utilizaremos Greasemonkey que debería inyectar nuestro archivo.js de módulo de WhatsApp para atraparlo y enviamos el enlace directo de la página final de phishing a la víctima. Si tienes dudas puedes consultarme a mi o ir al GitHub donde se explica un poco mejor además de estar la herramienta: [QRLJacking](https://github.com/OWASP/QRLJacking)

  

## ¡Ahora utilizaremos la herramienta!

### **Instalamos**

```bash
git clone https://github.com/OWASP/QRLJacking.git
```
  
Vamos a la carpeta de QRLJacking con cd y después nos vamos a la carpeta QRLJacking.Framework con cd e instalamos los requerimientos

  
```bash
pip install -r requirements.txt
```

¿Listo? Pues ¡Aprobarlo!

```bash
python QRLJacker.py
```

Ahora escomemos la opción 1 y después la 1 otra vez, ahora que -hayamos seleccionado WhatsApp para el ataque ponemos el puerto que usaremos (Pueden usar cualquiera) después no abrirá la web de WhatsApp esperamos que se cargue el código de sesión y después nos vamos a la página que nos pone la terminal que es el phishing. Recuerda si te sales de la web que te salió de primeras o la cierras no funcionara y tendrás que hacerlo de nuevo. Bien ya tenemos todo listo ahora usaremos la mejor herramienta que es nuestra mente para que la víctima escanee el código

 ![qrwas](/assets/img/post/10/qrwasap.jpg) 
 
**Escenario inreal, pero posible:**

**Atacante:** Hola, estoy dispuesto a hackear una cuenta de WhatsApp.
**Victima:** ¿Por qué?
**Atacante:** ¿Quieres sí o no? Puedo hacerle el trabajo a otro si quieres.
**Victima:** Noo, no te vayas y está bien este es el numero
**Atacante:** listo, ya pude este es el código (link)
**Victima:** ¡Gracias! Lo escaneare :3

**¡Misión completada!**

 ![qrwstmp](/assets/img/post/10/qrwstemplate.jpg)

Si quieren que se vea mas creíble editen el archivo phishing.html y póngale este: [Archivo.html](https://drive.google.com/file/d/15oHNAqFTRNEtT9XM3fVIZnIP0GLGWQ-A/view?usp=sharing) y se vera algo así:

 ![qrwstmp2](/assets/img/post/10/qrwstemplate2.jpg)

También este método se puede utilizar, utilizando otro ataque llamado **MITM** para que se redireccioné a una web o ponerle el código QR para que lo escanee, pero todo esto ya viene a tu imaginación y que puedas crear una buena trampa de pendiendo de la persona a quien se le ataque.