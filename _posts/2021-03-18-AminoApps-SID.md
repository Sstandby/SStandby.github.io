---
title: Como entrar a una cuenta de Amino.
date: 2021-03-18
categories: [Pentesting, Reversing]
excerpt: SID de AminoAPps
tags: [Reversing, API, RSS, AminoApps]
---

Este blog solo tiene fines de enseñaza al publico, no me hago responsable de su mal uso.

```
⠀⠀⠀ |\__/,| (`\
⠀⠀_.|o o |_ ) )
-(((---(((--------
```

Vean estos blogs como "preventivos" a x situaciones que explicare mas adelante, en si, esto es mas una clase de seguridad a los usuarios que no entienden tan bien el internet, o al menos no saben como operan webs ni apps.

**<center>୭̥*ೃ ❝lest go.. ♫</center>**

Cuando noosotros iniciamos sesion se crean header para la conexion, al igual para cuando cerramos sesion, algunas cosas siguen persistente y otras simplemente se borran del servidor y se crean nuevos datos al iniciar nuevamente sesion, para que entienda, voy a cerrar sesion y les mostrare los datos que me da.

![SID](/assets/img/post/28/sid1.jpg)

POST: https://service.narvii.com/api/v1/g/s/auth/logout

En donde sale la URL es la api de amino a la que la app manda la conexion o petecion, si no le enviamos nada de información no podriamos entrar a Amino. Para este ejemplo, la url indica que cerramos sesion.

-  **NDCLANG** Es la parte donde la app misma te indica que estas en el idioma español.
- **NDC-MSG-SIG** Gran parte o casi toda la "seguridad" de Amino, se encuentra en NDC-MSG-SIG. Luego hago un blog de como esto no estan seguro,
- **NDCDEVICEID** La mayoria de apps, por no decir todas se manejan de IDs, bueno en esta parte se encuentra el ID de tu telefono, es decir, que cuando entras Amino, tu telefono es registrado con tu cuenta, ¿Nunca te has preguntado como es que Amino no permite crear mas de 3 cuentas? es por esto mismo, le ponen limite a tu ID de telefono, pero si usas una app que clona Amino, ¿Sigue teniendo el mismo DEVICE ID? pues, no. Se crea uno virtual.
- **SMDEVICEID** Lo mismo, para que se den una idea, pueden encontrar el ID de sus dispostivos poniendo: `*#*#8255#*#*`
- **NDCAUTH** Todo paquete que tenga esto tendra la firma de Amino, el cual se encuentrado codificado en base64 (SI, BASE64, LMAO) el cual no es recomendado para usarse en cosas como estas, porque es lo mas inseguro que puede haber, tampoco se reconoce como un algoritmo de cifrado. Luego seguimos con este tema y como puede a tu cuenta con tu NDC-AUTH.
- **Accept.Languege** Es lo mismo que NDCLANG
- **Content-Type** Le dice al servidor que tipo de archivo sera retornado, es decir, luego de manda la solicitud la respuesta se convertira en un JSON que es como un archivo de texto organizado para intercambiar datos.
- **User-Agent** Es el registro de tu celular, como ves uso el sistema Android el cual contiene aparte de eso si se dan cuenta dice la ruta de la carpeta de Amino; Dalvik/2.1.0 (Linux; U; Android 5.1; XT1033 Build/LPBS23.13-56-2; com.narvii.amino.master/3.4.33564)

Y bueno lo demas lo demas es informacion a la cual como esta codificado y a que host ira (service.narvii.com)

> ¿Recuerdan lo de JSON que mencione anteriormente?

Una vez que le dimos dichos datos de conexión a Amino, prosigue darle la siguiente información para cerrar sesion:

```json
{
  "clientType": 100,
  "deviceID": "CENSURED",
  "timestamp": 1616103850230
}
```

El tipo de lectura que se hara con el cliente y serviro; 100. El deviceID que mencionamos anteriormente, y el timestamp, que es cuando comienza un evento, es decir, pone en segundos exactos (todo ese numero muestra mes, fecha, hora, etc. En segundos) a la hora de que subimos esta respuesta.

Respuesta del servidor al cliente una vez aceptado la info y la conexión que hicimos:


```json
{

  "api:duration": "0.119s",
  "api:message": "OK",
  "api:statuscode": 0,
  "api:timestamp": "2021-03-18T21:44:12Z",
  "auid": "c0884d27-5f07-4579-92bf-782563080c16"

}
```

Ahora que sabemos todo esto, sigue la parte de iniciar sesion.

> POST https://service.narvii.com/api/v1/g/s/auth/login

Ahora cambio la URL, ¿Recuerda el NDC-AUTH? bueno esa información cambio, pero lo demas sigue igual, ¿Por qué solamente cambio esto? pues, antes de decirles el por que esta fue la información que le di al servidor para entrar:

```json
{
  "action": "normal",
  "clientType": 100,
  "deviceID": "CENSURED",
  "email": "correo@gmail.com",
  "secret": "0 CONTRASEÑA",
  "timestamp": 1616107635519, 
  "v": 2
}
```

Y esta fue información que el servidor me mando como respuesta:

![SID2](/assets/img/post/28/sid2.jpg)

![SID3](/assets/img/post/28/sid3.jpg)


Sale toda la info de mi cuenta, no sale mucha por lo que mantengo todo seguro mientras estoy en Amino, no mantengo mi numero vinculado ni ninguna red socia, porque ya muchos han entrado a mi cuenta por discuido mio, y por curiosidad a la que me llevo a esto, en fin...

Toda esa información que puede tener alguien en caso de que acceda a tu cuenta, mediante al NDC-AUTH.

Esto crea una session en Amino, como una cookie, pero insegura, jaja. Al igual que una cookie, este SID o NDC-AUTH, se puede robar, no solo eso, se puede generar.

### ¿Como es un SID?
----

```ŧext
AnsiMSI6IG51bGwsICIwIjogMiwgIjMiOiAwLCAiMiI6ICI2ZDFkMmIzZS02YTg1LTRhYjktYTI2OC0xZWIzZGZhMWZmM2QiLCAiNSI6IDE2MTQ5NjMwNzEsICI0IjogIjM1LjE5My4xMTMuMjUzIiwgIjYiOiAxMDB90f4qOjk3EB1J547w-mmH9R0fj64
```

**Descifrado.**

```json
{"1": null, "0": 2, "3": 0, "2": "6d1d2b3e-6a85-4ab9-a268-1eb3dfa1ff3d", "5": 1614963071, "4": "35.193.113.253", "6": 100}Ñþ*:97Içðúiõ®
```

El comienzo Ansi, es la llave del SID, es decir, "{" y  MSI6IG51bGws es "1": null, y bueno ya se pueden dar una idea de lo demas, ahora expliquemos las cosas que nos dejan un poco confundidos, primero que todo ¿Qué es ese numero grande?, bueno ¿Recuerdan que hice un blog de como encontrar a cualquier usuario en Amino? pues, bueno en ese mismo blog les enseñe a sacar el ID de nuestra cuenta y el de cualquier cuenta (Tranquis, es legal, jaja) y bueno, ese ID "6d1d2b3e-6a85-4ab9-a268-1eb3dfa1ff3d", es de la cuenta victima (O sea mi multicuenta uwu).

El 1614963071 es el timestamp (Si comienza con 161 es un timestamp) que enseñe anteriormente,.

35.193.113.253 es la IP en donde inicie sesion, o sea desde la IP de un servidor de Amino,  y 6 debe ser el clienType, si se dan cuenta esta informacion esta organizada por numeros, y a esto le decimos "JSON", lo ultimo son bytes (No se mostraron todos por incompatibilidad con la web de Amino) que se genera cada vez que entramos a Amino, o sea es diferente, eso si, que sea diferente no significa que el anterior SID deje de servir. :)

### ¿Es seguro?
----

Claro que no. Fin del blog. Recuerden, al final lo unico que cambia de un SID es el ID de una cuenta el cual se puede tener facilmente con un click, y aparte de eso los ultimos bytes, de resto sigue igual, de hecho la IP da igual, solamente se toma como registro. Eso si, generar un SID es completamente imposible sin saber el key que usa el servidor para generar estos ultimos digitos dentro de la app y luego entrar, pero quien logre saberlo tendria el acceso total de cualquier cuenta, al final eso es teoria basica de cookies.

### ¿Como me protejo de un posible ataque de robo de SID?

Simple, si alguien les dice que entren aun ndc y les mande captura, no lo hagan, el ndc puede ver así: ndc://fragment/com.narvii.util.debug.DebugInfoFragment, igual ya saben si tiene de nombre SID= o DEVICEID= no lo muestre, ni entren a links extraños, pueden sufrir de un clickjacking, lo explique en mi primer blog de como entrar a una cuenta de Amino. Ademas de eso, cuando no usen la app por las noches, cierren session, para que el timestamp caduque, y cuando vuelvan hacer otra session en Amino para generar otro cuando se despierten.

Aparte de esto, cuando inicias sesion con un SID la información que les mostre antes cuando inicias sesion con correo y contraseña, no es la misma, se limita a mostrarte toda esa información.

![SID4](/assets/img/post/28/sid4.jpg)
