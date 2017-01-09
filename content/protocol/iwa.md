---
date: 2017-01-07T16:56:39Z
title: Protocolo Iwa
---

**IWA** es el protocolo base para establecer una comunicacion entre el *widget* y el *contenedor*.
Funciona a traves de [```Window.postMessage()```](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage).
La comunicacion se estblecera por **canales** que seran privados para cada **Wdiget**. Cada canal tendra una api asignada por lo que se recomienda poner nombres largos y poco comunes para evitar conflictos. Nombres de canales ya asignados a los extras de FIWA: *extraiwa, extraplayer, extragame, extramap*.

## Iwa en la parte del contenedor
Cuando un widget es cargado iwa debera realizar una serie de acciones, llamadas **Acciones de registro de widget**

### Acciones de registro de widget
Primero debera registrar el id y la URL necesario para acceder al widget en una lista (*EJ: un Array*).

Despues debera inyectarle el siguiente codigo **HTML** al pricipio de la etiqueta ```<body>``` :
```
<script>var parenturl = //contenedorURL//;</script>
```
**Donde pone ```//contenedorURL//``` hay que sustituirlo por la URL del contenedor**, esto es debido a que iwa usa la funcion
```
Window.postMessage()
```
para enviar los mensajes entre el contenedor y los widgets. *Si el contenedor no tiene una url, osea que no es una pagina web, se debera usar una url de referencia, podria ser la url de la pagina del desarollador por ejemplo.*

Se pueden añadir acciones extras a este conjunto, *Ejemplo: cambiar el color de fondo del widget.*, siempre y cuando no afecte a la comunicacion normal.
___
Despues de esto, cuando el contenedor reciba un paquete, el mensaje tendra el sigiuente formato:
### Formato del paquete recibido
Se recibira un **Array** y cada posicion(key) sinificara lo siguiente.

| posicion(key)  | valor           |
| :------------- | :-------------- |
| 0              | Nombre del canal|
| 1              | mensaje         |
| 2              | *No asignado, dejar en null*|
| 3              | Nombre y version de la api separada por -, *Ejemplo: extraiwa-1.0*|
| 4              | Formato de los mensajes, *Ejemplo: xml, json, YAML*|
Los parametros **3 y 4** el widget tiene la obligacion de enviar estos parametros si envia el parametro mensaje sin nada, osea **Nulo**. Normalmente el **widget** enviara un mensaje nulo con los parametros **3 y 4** al inicio.

La api solo le dara importancia al parametro **3** si no es retrocompatible con versiones anteriores o futuras a la suya, debido a que en un canal solo tiene que ser usado por una api o protocolo.

Este paquete no se tiene que extender, lo que sinifica que no se podran añadir parametros extras.
___

Si el contenedor desea enviar un paquete al widget, tiene que tener el siguiente formato:
##Formato del paquete a enviar
Se enviara un **Array** y cada posicion(key) sinificara lo siguiente.

| posicion(key)  | valor           |
| :------------- | :-------------- |
| 0              | Nombre del canal|
| 1              | mensaje         |

Este paquete no se tiene que extender, lo que sinifica que no se podran añadir parametros extras.

___
