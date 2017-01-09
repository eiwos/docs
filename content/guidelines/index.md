---
date: 2017-01-07T16:39:43Z
title: Directrices
---
Estas son las directrices que deben seguir tando el **container** *(pagina o app que contiene el widget)* como
el **widget**. Las directices que esten completamente en *cursiva* no es obligatorio seguirlas pero si recomendado.
___

## Directrices para el container

1. Ser compatible al 100% con el protocolo [FIWA]({{< ref "protocol/index.md" >}}) y comunicarse con los iframes a traves de este.
2. El objeto incrustado (*Ejemplo: iframe*) donde se encuentre el widget debera permitir la trasparencia. *Ejemplo:* ```
<iframe width="" height="" src="" **allowtranspatency="true"**></iframe>
```
3. El objeto incrustado (*Ejemplo: iframe*) donde se encuentre el widget debera ejecutar el widget en una [**sandbox** o aislamiento de proceso](https://es.wikipedia.org/wiki/Aislamiento_de_procesos_(inform%C3%A1tica)).
*Ejemplo:* ```<iframe width="" height="" src="" **sandbox="permisos"**></iframe> ```
Y debera darle los permisos que el widget requiera , el usuario permita y no afecten a la seguridad del contenedor.
4. El objeto incrustado (*Ejemplo: iframe*) donde se encuentre el widget no debe mostrar las barras de scrolling.  *Ejemplo:* ```<iframe width="" height="" src="" **scrolling="false"**></iframe> ```

___
## Directrices para el widget

1. Ser compatible al 100% con el protocolo iwa y extraiwa.
2. Usar el protocolo [extragame]({{< ref "protocol/extras.md#game" >}}) para los videojuegos, [extraplayer]({{< ref "protocol/extras.md#player" >}}) para reproductores de audio/video, [extramap]({{< ref "protocol/extras.md#map" >}}) para mapas y asi sucesivamente con los demas protocolos extra de [FIWA]({{< ref "protocol/index.md" >}}).
3. Usar [OEmbed](http://oembed.com/) y usando los parametros del [modelo estandar oembed de eiwos](/Oembed-model.html).
4. El diseño web tiene que ser [responsivo](https://es.wikipedia.org/wiki/Dise%C3%B1o_web_adaptable), hay que pensar que el widget
sera incrustado en espacios pequeños.
5. No almacenar ningun tipo de cookie ni de terceros.
6. Si se incluye publicidad, debera seguir las directrices de [publicidad aceptable *de adblockerplus*](https://adblockplus.org/es/acceptable-ads) y no podran ocupar mas del 15% de la pagina. Si el widget es una publicidad no es obligatorio seguir esta directriz.
7. Solo se permiten enlaces externos que se abran en una nueva pestaña.
8. Solo abrir popups si el usuario quiere y esta informado de que se va abrir un popup y del contenido de este popup.
9. *Evitar footers, barras superiores, contenido flotante, el widget tiene que tener una interfaz directa y clara para el usuario, sin contenido extra.*
