---
layout: post
title: Actualiza tu biblioteca música en cmus
description: Aprende a automatizar la actualización de tu biblioteca de música en el reproductor de terminal cmus mediante un script y cmus-remote.
summary: Guía práctica para crear un script en Bash y configurar un atajo de teclado que limpie, añada y actualice la caché de cmus automáticamente.
comments: true
tags: [Linux, Mac, Tutoriales]
---

Hace unos días hablábamos de [cmus](https://andriuzha.github.io/2025/04/15/cmus-el-reproductor-de-musica), un excelente reproductor de música por terminal. Hoy veremos como podemos actualizar la biblioteca de música de una forma sencilla, debido a propia la naturaleza del reproductor todo se realiza por comandos, así que simplifiquemos el proceso.

## ¿Qué haremos?

Necesitaremos crear un pequeño script que automatice la secuencia que deberíamos de seguir, que a saber es la siguiente:

* `:clear` Borra toda la biblioteca de música.
* `:add /directorio/musica` Agrega todas las canciones que encuentre en este directorio.
* `:update-cache -f` Forza la caché de toda la biblioteca.

Recuerda que esto es una guía y deberás de colocar las rutas de los directorios donde desees guardar el script y colocar las rutas donde tienes almacenada la música.

Ahora, únicamente necesitamos hacer que pase, lo primero es entender qué hace `cmus-remote`.
`Cmus-remote` es una herramienta que nos permite controlar el reproductor de música de forma remota, esto significa que ¡podríamos usar una aplicación o script incluso de otro dispositivo para pausar, reproducir, saltar canciones, ajustar el volumen y otras funciones de cmus!, sin tener que interactuar directamente con el terminal donde se está ejecutando el reproductor. Aunque en este caso lo utilizaremos dentro del propio terminal, pero con `cmus-remote` se abre una serie de oportunidades.

## Creando el script

Primero generamos un archivo de texto para el script, tanto en macOS como en Linux, la carpeta de configuración, listas de reproducción, y personalizaciones que se pueden realizar están en la carpeta de usuario `.config` (que está oculta), así que yo crearé ahí mi archivo, para ello utilizaré `vim`, pero puedes utilizar `nano`. Abrimos la terminal y colocamos:

```bash
vim ~/.config/cmus.update.sh

```

Dentro colocamos el siguiente script:

```bash
#!/bin/bash
cmus-remote -C clear
cmus-remote -C "add ~/directorio/musica/"
cmus-remote -C "update-cache -f"

```

Que son los mismos comandos que vimos al inicio, ahora solo tenemos que darle permisos de ejecución:

```bash
chmod +x ~/.config/cmus.update.sh

```

Ahora solo nos resta decirle a cmus que queremos iniciar el script asignándole un atajo de tecla, en este caso será `u`, que si bien ya está asignada a la actualización de la caché, la utilizaremos porque es fácil de recordar y en el propio script ya forzamos esa actualización. Si quieres cambiar la tecla de atajo, puedes hacerlo, solo asegúrate que no entre en conflicto con otra. Puedes revisar [el manual en este sitio](https://linux.die.net/man/1/cmus) o colocando el comando `man cmus` en tu terminal.

```bash
:bind -f common u shell ~/.config/cmus.update.sh

```

Y eso es todo, ahora puedes realizar la actualización de tu biblioteca a golpe de una sola tecla.

