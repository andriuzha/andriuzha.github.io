---
layout: post
title: Moviendo archivos de subcarpetas a toda velocidad (Linux)
description: Aprende a mover o copiar archivos desde múltiples subcarpetas a un solo directorio usando la terminal en Linux y macOS.
summary: Guía rápida para utilizar find y mv con la opción de respaldo numerado para extraer archivos de subcarpetas anidadas de forma masiva y segura.
comments: true
tags: [Linux, Tutoriales]
---

Ayer tuve que mover, por motivos de políticas de respaldo - ya estamos cerca del fin de año - una cantidad ingente de archivos. Estos archivos estaban anidados en muchas subcarpetas, pero a mi solo me interesaba guardar los archivos sin conservar la estructura de las carpetas. Claro que podemos abrir el explorador de archivos e ir navegando entre los archivos para cortarlos y pegarlos dentro de otra carpeta, pero eso toma mucho tiempo y es aburrido, además estamos en Linux y con la Terminal podemos hacerlo en unos momentos,veamos cómo se hace:

## Consideraciones

Una consideración antes de esto, no sabía la cantidad concreta de archivos que se tenían y tampoco si estos estaban repetidos a lo largo de las carpetas, así que primero moveremos todos los archivos sin las carpetas a un solo directorio, además conservaremos los archivos en caso de tener los nombres duplicados, para asegurarnos que no borramos nada importante, después podemos filtrarlos para eliminar los duplicados, pero seriá tema de otra entrada.

El comando que tenemos que ejecutar es el siguiente:

```bash
find /directorio/origen -type f -exec cp --backup=numbered -t /directorio/destino {} +

```

## Entendamos que estamos haciendo

**`find`** es el comando encargado de encontrar cosas, con la bandera **`-type f`** especificamos que se tratan de archivos.

**`cp`** es el comando que copiará todos los archivos encontrados por **`find`** y **`--backup=numbered`** se encargará renombrarlos, enumerándolos si se encontrarán dos archivos en el mismo nombre.

**`-exec`** sirve para enviar la salida de un comando como una secuencia del primer proceso, evitando que se inicien dos procesos para una sola acción.

**`{} +`** son opciones especificas de **-exec**, las llaves son para indicar que se trabaje con el nombre del archivo que se está procesando y el signo más es para reducir la cantidad de argumentos con los que se trabaja.

**`/directorio/origen`** y **`/directorio/destino`** son evidentes.

## Personalizando el comando

En caso que sólo necesitemos copiar un tipo de archivo en un montón de carpetas y subcarpetas, le indicaremos a find que tipo de archivos queremos encontrar, mediante su extensión con la bandera `-iname "*.xyz"`, de forma que si queremos solo los archivos pdf el comando quedaría:

```bash
find /directorio/origen -type f -iname "*.pdf" -exec cp --backup=numbered -t /directorio/destino {} +

```

En caso de querer mover los archivos reemplazamos el comando copiar por mover

```bash
find /directorio/origen -type f -iname "*.pdf" -exec mv --backup=numbered -t /directorio/destino {} +

```

Solo bastaría esperar unos segundos y los archivos estarían en la nueva carpeta.
