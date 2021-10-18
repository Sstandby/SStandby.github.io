---
title:  Rastreo fotográfico
date: 2018-12-30
categories: [Pentesting, Herramientas]
excerpt: Rastreo por imagen
tags: [OSINT]
---  

Usaremos una herramienta llamada "EaglEye" lo único que tenemos que tener o darle a EagleEye es la foto de la víctima y nombre después lo que hará es hacer un reconocimiento facial a cada perfil de facebook hasta encontrar a esa persona y luego usa Google y ImageRaider Reverse Image Search para encontrar esa persona en otras redes sociales ya que termine todo este rollo nos dará un informe en modo PDF

### Instalación automatizada:
----
```bash
wget https://raw.githubusercontent.com/ThoughtfulDev/EagleEye/master/install.sh && chmod +x install.sh && ./install.sh
```

### Instalación manual basadas en distribuciones en Debian
---
```bash
$ sudo apt update && sudo apt upgrade -y

$ sudo apt install git python3 python3-pip python3-dev

$ sudo apt install libgtk-3-dev libboost-all-dev build-essential cmake libffi-dev

$ git clone https://github.com/ThoughtfulDev/EagleEy

$ cd EagleEye && sudo pip3 install -r requirements.txt

$ sudo pip3 install --upgrade beautifulsoup4 html5lib spry
```

**Arch**

```bash
$ sudo pacman -Syu

$ sudo pacman -S git python python-pip gtk3 boost cmake libffi

$ git clone https://github.com/ThoughtfulDev/EagleEye

$ cd EagleEye && sudo pip3 install -r requirements.txt

$ sudo pip3 install --upgrade beautifulsoup4 html5lib spry
```

Recuerda tener instalado Firefox y si ya lo tienes asegúrate tener instalado Geckodriver en su última versión para su arquitectura y si tesale broken pipe ERROR utiliza la versión de Geckodriver 0.19.1. También si tienes kali linux y tienes Firefox ESR utiliza la versión 17 de

### Instalación de Geckodrive  
----
```bash
wget https://github.com/mozilla/geckodriver/tags
sudo sh -c 'tar -x geckodriver -zf geckodriver-*.tar.gz -O > /usr/bin/geckodriver'
sudo chmod +x /usr/bin/geckodriver
```

Ahora cambia el valor en config.json la ruta del geckodriver

```bash
{

"DEFAULTS": {
"SLEEP_DELAY": "7",
"GOOGLE_IMG_PAGES": "3"
},

"WEBDRIVER": {
"ENGINE": "firefox",
"PATH": "/usr/bin/geckodriver"
},

"FILTER": [
"instagram.com",
"twitter.com",
"pinterest.com",
"plus.google.com"
],

"INSTA_VALIDATION_MAX_IMAGES": "5"
}
```

Hacer el Geckodriver ejecutable

```bash
chmod +x /path/to/geckodriver
```

Para usar la herramienta

```bash
python3 eagle-eye.py
```

Para ver una lista de todas las opciones disponibles

```bash
python3 eagle-eye.py -h
```

![captura](/assets/img/post/07/captura.jpg) 
 
![captura2](/assets/img/post/07/captura2.jpg) 