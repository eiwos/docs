---
date: 2017-01-07T16:56:33Z
title: Protocolos extras
---
## Extraiwa

Protocolo que funciona sobre iwa, por el canal **extraiwa**, usando el formato **Json** y esta diseñado para ser
**Retrocompatible** con versiones anteriores y futuras de este.
Este protocolo deberia ser utilizado **siempre** por el widget, ya que da funcionalidades de uso comun entre los varios protocolos
extras.
___

Cuando el widget termina de cargar(*DOMContentLoaded*), enviara el siguiente mensaje:
### Mensaje de widget cargado
Parametros del Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | loaded         |
___

Cuando el contenedor termine de cargar(*DOMContentLoaded*), enviara el siguiente mensaje:
### Mensaje de contenedor cargado
Parametros del Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | loaded         |
___

Cuando un usuario empieza a interactuar con un widget, o el widget empieza a reproducir un contenido multimedia o juego etc...
Enviara el siguiente mensaje:
### Mensaje de widget ejecutandose
Parametros del Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | playing        |
___

Cuando un usuario deja de interactuar con un widget o el widget deja de reproducir un contenido multimedia o juego etc...
Enviara el siguiente mensaje:
### Mensaje de widget a parado de ejecutarse
Parametros del Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | finish         |
___

## Game

Protocolo que funciona sobre iwa, por el canal **extragame**, usando el formato **Json** y esta diseñado para ser
**Retrocompatible** con versiones anteriores y futuras de este.
Este protocolo deberia ser utilizado **solo** cuando el widget es un videojuego.
___
## Mensajes de inicio.
Nada mas terminarse de iniciarse el widget deberia enviare los siguientes mensajes:
### Informacion del juego
se especificara informacion acerca del juego,

**Tabla de paramatros de informacion:**

| Parametro      | Valor          |
| :------------- | :------------- |
| name           | *Nombre del juego* |
| description    | *Descripcion del juego* |
| author         | *Autor del juego* |
| url            | *link a la pagina desarolladora del juego* |
| type           | *tipo de juego* |
| age            | *edad recomendada para el juego* |
| [NSFW](https://es.wikipedia.org/wiki/NSFW) | true *o* false |
| multiplayer    | true *o* false |
| local_multiplayer | true *o* false |
| doublecheck **ignorar** | true *o* false |



Se pueden enviar parametros adicional no especificados en esta tabla.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_game_info  |
| info_keys      | *Array de strings con los nombres de los parametros de informacion* |
| info_values    | *Array de strings con los valores de los parametros de informacion, ordenados como los info_keys* |

### Controles del juego
se especificara los controles del juego y la tecla al que esta asignado cada uno,

**Tabla de controles:**

| Control        | Sgnificado     |
| :------------- | :------------- |
| jump           | *saltar*       |
| left           | *ir hacia la izquierda* |
| right          | *ir a la derecha* |
| up             | *subir*         |
| down           | *bajar*         |
| atack          | *atacar*        |
| interact       | *interactuar*   |
| pause          | *poner en pausa*|
| ability_1      | *habilidad 1*   |
| ability_2      | *habilidad 2*   |
| ability_x      | *habilidad x*   |
Se pueden enviar parametros adicional no especificados en esta tabla.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_controllers|
| controllers_names | *Array de strings con los nombres de los controles disponibles* |
| controllers_keys | *Array de strings con las teclas asignadas a cada control, ordenados como los controllers_names* |
__

Ademas el widget podra enviar los siguintes mensajes:

### Actualizar tabla de posiciones
Se enviara cada vez que la tabla de posiciones cambie, la tabla puede tener la medida que se desee pero se recomienda solo poner
los diez mejores jugadores.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_leadboard|
| leadboard_names | *Array de strings con los nombres de los mejores jugadores* |
| leadboard_values | *Array de int con las puntuaciones de esos jugadores, ordenados como los leadboard_names* |
__

### Actualizar el valor de un valor
Se enviara cada vez que un valor cambie.

**Tabla de valores:**

| nombre         | Sgnificado     |
| :------------- | :------------- |
| money          | *dinero*       |
| highscore      | *puntuacion mas alta del jugador* |
| best_higscore  | *puntuacion mas alta obtenida por algun jugador* |
| score          | *puntuacion actual* |
Se pueden enviar parametros adicional no especificados en esta tabla.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_value   |
| value_name     | *Nombre del valor* |
| value          | *Valor* |
__

### Se esta jugando desde un movil o tablet
Este valor se envia cuando el juego activa los controles tactiles porque ha detectado que se esta jugando desde un movil o tablet.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_phone      |
| value_name     | *Nombre del valor* |
| value          | *Valor* |
__

Mientras que el contenedor podra enviar los siguientes mensajes:

### Cambiar tecla de un control
Se enviara cuando el container desee cambiar la tecla asignada a un control.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_controller |
| name           | *Nombre del control* |
| key            | *Tecla* |
__

### Forzar a mostrar o ocultar los controles de movil

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_phone_controller |
| show           | true *o* false |
__

### Poner estilo
Se enviara una hoja de estilo para los controles de movil, todos los controles de movil estaran dentro de la clase controllers,
el nombre de la clase de cada controller corespondera con el nombre asignado en la tabla de controles (*mire arriba*)

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_css        |
| css            | *Hoja de estilo* |
__

### Usuario
Se enviara para asignar un nombre de usuario y una sesion

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_user       |
| name           | *Nombre de usuario* |
| session        | *Token de sesion* |
__

## Player
Protocolo que funciona sobre iwa, por el canal **extraplayer**, usando el formato **Json** y esta diseñado para ser
**Retrocompatible** con versiones anteriores y futuras de este.
Este protocolo deberia ser utilizado **solo** cuando el widget es un reproductor de videos, audio o otro tipo de multimedia.
___
## Mensajes de inicio.
Nada mas terminarse de iniciarse el widget deberia enviare los siguientes mensajes:
### Actualizar fuentes
Este mensaje contendra todas las fuentes(*Youtube, vimeo, soundclound, localmp4*) que el reproductor acepta, este mensaje se tiene
que enviar al inicio pero, se puede volver a mandar.

**Tabla de fuentes:**

| Nombre         | tipo           | nota                                    |
| :------------- | :------------- | :-------------------------------------- |
| youtube        | Video          | el media id tiene que ser el id del video de youtube|
| vimeo          | Video          | el media id tiene que ser el id del video de vimeo|
| soundcloud     | Audio          | el media id tiene que ser el enlace del audio de soundcloud|
| urlv*tipo*  | Video          | en donde pone *tipo* sera sustituido por el formato del video(*mp4, webm...*), el media id sera el enlace **directo** hacia el video|
| urla*tipo*  | Audio          | en donde pone *tipo* sera sustituido por el formato del audio(*mp3, flac...*), el media id sera el enlace **directo** hacia el audio|
Se pueden poner fuentes que no salen en esta tabla, pero usar un nombre claro y directo, *Por ejemplo: si la fuente es twich,
poner de nombre **twich**, no poner Twich, twichmedia, ...*

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_sources |
| sources        | *Array de strings con los nombres de las fuentes soportadas* |

__

### Poner calidades
Este mensaje contendra todas las calidades disponibles en el reproductor, se debera enviar cuando un multimedia es cargado.

**Tabla de calidades:**

| id  | calidad video  | calidad audio |
| :-- | :------------- | :------------ |
| 0   | 96p            | 32 Kbps       |
| 1   | 120p           | 96 Kbps       |
| 2   | 144p           | 128 Kbps      |
| 3   | 240p           | 128 Kbps      |
| 4   | 360p           | 192 Kbps      |
| 5   | 480p           | 192 Kbps      |
| 6   | 720p           | 192 Kbps      |
| 7   | 1080p          | 320 Kbps      |
| 8   | 2160p          | *Mayor que 320kbps* |
| 9   | 4320p          | *Mayor que 320kbps* |
Si el contenido multimedia es un video pero incluye audio, no tiene porque seguir las calidades de audio.
Las calidades de audio se pueden seguir de forma aproximada es decir, un video con calidad **7** puede ser 1090p.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_qualities |
| sources        | *Array de **int** con las id de las calidades disponibles* |

__

### Cambiar contenido multimedia
Este mensaje se enviara caundo un nuevo archivo multimedia es cargado, y contendra informacion sobre este.

**Tabla de paramatros de informacion:**

| Parametro      | Valor          |
| :------------- | :------------- |
| name           | *Nombre del media* |
| description    | *Descripcion del media* |
| author         | *Autor del media* |
| url            | *link al media original* |
| id             | *id del media* |
| source         | *nombre de la fuente del video* |
| createon       | *fecha de creacion del video, formato: **dd:mm:aaaa*** |
| subtitles_langs| *[codigo de idioma](https://es.wiktionary.org/wiki/Wikcionario:Códigos_de_idioma)* |
| audio_langs    | *[codigo de idioma](https://es.wiktionary.org/wiki/Wikcionario:Códigos_de_idioma)* |
| [NSFW](https://es.wikipedia.org/wiki/NSFW) | true *o* false |
Se pueden enviar parametros adicional no especificados en esta tabla.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_media   |
| duration       | *duracion en segundos del contenido multimedia* |
| info_keys      | *Array de strings con los nombres de los parametros de informacion* |
| info_values    | *Array de strings con los valores de los parametros de informacion, ordenados como los info_keys* |

__

### Poner controles
Este mensaje se enviara solo al pricipio con los cotroles disponibles y sus valores iniciales.

**Tabla de controles:**

| nombre         | Valor          |
| :------------- | :------------- |
| volumen        | *volumen del 0 al 100* |
| quality        | *id de la calidad actual, vease tabla de calidades* |
| speed          | *numero entero, se multiplicara la velocidad por este numero* |
| subtitles      | true *o* false |
| subtitles_lang | *[codigo de idioma](https://es.wiktionary.org/wiki/Wikcionario:Códigos_de_idioma)* |
| audio_lang     | *[codigo de idioma](https://es.wiktionary.org/wiki/Wikcionario:Códigos_de_idioma)* |
Se pueden enviar parametros adicional no especificados en esta tabla. No enviar parametros que el reproductor no permita cambiar.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_controls|
| controls       | *Array de strings con los nombres de los controles* |
| controls_values| *Array de strings con los valores de los controles, ordenados como los controls* |
___

Ademas el widget podra enviar los siguintes mensajes:

### Cambiar estado:
Este mensaje sera enviado cuando el estado del reproductor cambie,

**Tabla de estados:**

| id  | Significado    |
| :-- | :------------- |
| 0   | no esta reproduciendo nada |
| 1   | reproduciendo |
| 2   | en pausa |
| 3   | cargando |
| 4   | error al reproducir |

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_status  |
| status         | *id del estado actual* |
__

### Cambiar tiempo:
Este mensaje sera enviado cada vez que el reproductor avance de segundo,

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_time    |
| time           | *segundo actual por el cual va el reproductor* |
__

### Cambiar valor de un control:
Este mensaje sera enviado cada vez que un control cambie de valor(*por el usuario, etc ...*),

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | update_control |
| control        | *nombre del control* |
| value          | *valor del control* |
__

Mientras que el contenedor podra enviar los siguientes mensajes:

### Cambiar estado:
Este mensaje sera enviado cuando el contenedor quiere cambiar el estado del reproductor,

**Tabla de estados que se pueden enviar:**

| id  | Significado    |
| :-- | :------------- |
| 0   | no reproducir nada |
| 1   | empezar a reproducir |
| 2   | poner en pausa |

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_status  |
| status         | *id del estado al que se quiere cambiar* |
__

### Ir al segundo:
Este mensaje sera enviado cuando el contenedor quiere ir a un segundo especifico,

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_time    |
| time           | *segundo al que se quiere ir* |
__

### Cambiar valor de un control:
Este mensaje sera enviado cuando el contenedor quiere cambiar el valor de un control,

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_control_value |
| control        | *nombre del control* |
| value          | *valor del control* |
__

### Cambiar contenido multimedia
Este mensaje se enviara caundo el contenedor desea cambiar el contenido multimedia del reproductor.

Parametros del mensaje en Json:

| Parametro      | Valor          |
| :------------- | :------------- |
| msg            | set_media      |
| source         | *nombre de la fuente* |
| media_id       | *dependera de la fuente puede ser una id o una url ...* |
