---
date: 2017-01-07T16:47:13Z
title: Modelo estandar para peticiones Oembed
---

[**OEmbed**](http://oembed.com/) es un poderoso formato que permite incluir contenido en paginas de terceros a traves de una URL.
Nos permite especificar el tipo de recurso, existiendo tres imagen, video y rich.
Rich nos permite incluir widgets pero para que funcionen corectamente eiwos especifica unos parametros adicionales para Oembed.
## Parametros adicionales
|nombre parametro| obligatorio? |  valor     | descripcion      |
| :------------- | :----------- | :--------- | :--------------- |
| width          | Si           | [vw](http://www.w3schools.com/cssref/css_units.asp)| anchura del widget |
| height         | Si           | [vh](http://www.w3schools.com/cssref/css_units.asp)| altura del widget  |
| URL            | Si           |            | enlace al contenido del widget  |
| perms          | Si           | [sandbox atributte values](http://www.w3schools.com/tags/att_iframe_sandbox.asp#Attribute%20Values)| permisos que necesita el iframe  |

Estos son los parametros adicionales que debera devolver la pagina al hacer una consulta Oembed.
## Todos los parametros
Estos son todos los parametros que se deben incluir de forma obligatoria.

|nombre parametro |  valor     | descripcion      |
| :-------------  | :--------- | :--------------- |
| width           | [vw](http://www.w3schools.com/cssref/css_units.asp)| anchura del widget |
| height          | [vh](http://www.w3schools.com/cssref/css_units.asp)| altura del widget  |
| URL             | una url    | enlace al contenido del widget  |
| perms           |  [sandbox atributte values](http://www.w3schools.com/tags/att_iframe_sandbox.asp#Attribute%20Values)| permisos que necesita el iframe  |
| version         | 1.0        | version formato oembed, siempre 1.0 |
| type            | rich       | tipo de contenido, siempre rich     |
| html            | un iframe con el widget | este valor es ignorado por las paginas compatibles con eiwos pero las que no usaran este html |
