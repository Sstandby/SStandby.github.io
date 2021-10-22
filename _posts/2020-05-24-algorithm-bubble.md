---
title: Ordenamiento por Método Burbuja. Aberración.
date: 2020-05-24
categories: [Programación, algorithm, C++]
excerpt: Aprendiendo un poco de C++
tags: [C++, Algoritmos]
---

### ¿Qué significa y como funciona Método burbuja?
---

Este metodo es uno de tantos para organizar elementos de maneras sencilla y fácil, y uno de tantos que no recomiendo. Su funcionalidad es hacer una comparación con cada elemento adyacente de la lista e intercambiando de posición si este esta en una equivocada.

En cosas sencillas como intercambiar variables con otras, por ejemplo, 2 con 1, no es necesario realizar los demás pasos que luego se irán mostrando, por ahora sera mas sencillo. Para esto simplemente hacemos una 3 variable la cual es la auxiliar de alguna de las anteriores variables ya sea 2 o 1.

Lo que no se debe hacer.

![burbuja](/assets/img/post/24/burbuja.jpg)

Este seria lo que no se debe hacer para un intercambiar una variable con otra, pues, si lo ejecutamos simplemente nos dará: 2, 2.  
  
![burbuja2](/assets/img/post/24/burbuj2.jpg)

Y esto no es intercambiar variables solo es sobre poner una encima de otra, eliminando el valor anterior de la variable que era 1, y ahora es 2. Aquí llegaría la 3 variable.

### Metodo Burbuja  
----

![burbuja3](/assets/img/post/24/burbuja3.jpg)

Como vemos se realizo el intercambio de variables, pues ahora si no esta sobre poniendo una encima de otra sino que ahora la 3 variable guarda el valor de la primera variable para que no se pierda en el proceso, y ya es posible intercambiar el valor de los dos.

### Arreglos unidimensionales.
---

Les mostrare el proceso que hace el Método burbuja para organizar arreglos unidimensionales, paso a paso, el proceso es sencillo, si miran el siguiente ejemplo del arreglo[5] = {5,4,3,2,1}, es decir, que si tenemos 5 elementos, habrán (5-1 o n-1) de parejas que se irán organizando por comparaciones (Los elementos con [] significan que se están comparando entre ellos). Sino es menor o igual 5 de 4 entonces 4 esta en una posición errónea, si no es menor o igual 5 de 3, entonces están en una posición errónea, también se puede describir de otra forma, si 2 no es mayor que 5 o igual (arr[i] > arr[i+1]) entonces esta en una posición errónea, etc.. Esto sera hasta que todos los números estén orden.

```text
[54]321

4[53]21

43[52]1

432[51]

432[15]

4[31]25

[41]325

1[43]25

....

..

..

[12345]
```


![burbuja4](/assets/img/post/24/burbuja4.jpg)
  
Les recomiendo usar n-1, aunque no sea obligatorio hacen de su codigo mas estable y optimizando ya que sino lo ponen solo hacen que hagan comparaciones innecesarias ya después de acabar (No aplica en todos los compiladores como Dev-C++, pero si en Code::blocks)
  
![burbuja5](/assets/img/post/24/burbuja5.jpg)


### Conclusión.
---

No lo usen. No es muy practico a la hora de ejecutarse, por lo que es un método muy lento y su realización de organizar los elementos es igual de lenta o hace tantas comparaciones que es muy innecesario, pero para los que están comenzando y lo ven muy sencillo (Porque lo es) pueden usarlo, pero ya les digo que si se quieren volverse profesionales no se los recomiendo su utilidad es nula y no es vista en ámbitos profesionales, solamente es recomendable para tener una idea de los bastantes algoritmos curisoso que existen. ~

- Oupot: [https://failingdeepskybluebaitware.standbyme.repl.run/](https://failingdeepskybluebaitware.standbyme.repl.run/)
- Codigo: [https://repl.it/@Standbyme/FailingDeepskyblueBaitware](https://repl.it/@Standbyme/FailingDeepskyblueBaitware)