---
title: AminoApps vulnerable? xd
date: 2019-03-16
categories: [Pentesting, Reversing]
excerpt: Explorando el funcionamiento de la API AminoApps
tags: [API, HTTPS]
---

Estaba perdiendo el tiempo otra ves y me di cuenta que puedo acceder a los blogs de otras personas mediante el metodo get.  
  
Primero debemos tener al alcance de nosotros una extensión/app para ver en vivo todo lo que pasa en la web, yo uso esta que es de chrome: [HTTP Headers](https://chrome.google.com/webstore/detail/http-headers/fabjnpecogealbfoebkcjfbmdhnnfhbj). Para [Firefox](https://addons.mozilla.org/es/firefox/addon/http-header-live/). Bueno una ves que la tengamos descargada la herramienta vamos a ejecutarla e iremos a un blog de nosotros dándole a editar.  
  
![Amino](/assets/img/post/20/amino1.png)

Vamos a la herramienta donde esta capturando todo lo que esta pasando en la web de Aminoapps, una ves dentro vamos a buscar la palabra "Amino" o "compose-post"  
  
![Amino2](/assets/img/post/20/amino2.png)

Este seria el link de esta comunidad: https://aminoapps.com/partial/compose-post?ndcId=44135535&type=edit&postId=dce212e9-7e4d-4d78-92f9-e87f9550fb8d&postType=blog y el del blog.  
  
![Amino3](/assets/img/post/20/amino3.png)

Yo puedo acceder, editarlo, y guardarlo, vosotros, solo pueden acceder, editarlo, pero no guardarlo o publicarlo, ¿Por que? Amino tiene que verificar que ustedes son yo (Tendrán que editar o hacer algo para hacerse pasar por el usuario ya sea mediante cookies que ya probé y funciono, así que les dejo esto mas como tarea)  
  
Cada comunidad y blog tiene su id, pueden ver el codigo fuente de algun blog y poner `post-id` y le saldrá (En mi caso) `dce212e9-7e4d-4d78-92f9-e87f9550fb8d` y el id de la comunidad si o si es con el HTTP header. (El de esta comunidad seria: 44135535)  
  
> https://aminoapps.com/partial/compose-post?ndcId=ID DE LA COMUNIDAD&type=edit&postId=ID DEL BLOG&postType=blog   
 
![Amino_3](/assets/img/post/20/amino3.png)
  
Por ejemplo, tengo el id de la comunidad que es 44135535 y el id de acceder al blog ya lo tengo solo falta el id del blog victima que sera el de kran.

![Amino_4](/assets/img/post/20/amino4.png)
![Amino_5](/assets/img/post/20/amino5.png)
  
"Si no puedo cambiar el pasado, me lo llevaré conmigo hasta la tumba."