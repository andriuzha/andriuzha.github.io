---
layout: post
title: Moviendo archivos a un directorio superior
description: Aprende a mover archivos desde subcarpetas anidadas a un directorio superior utilizando la terminal en Linux y macOS de forma rápida.
summary: Guía rápida para organizar archivos y subcarpetas caóticas moviéndolos a un directorio superior mediante comandos de terminal con find y xargs.
comments: true
tags: [Linux, Tutoriales]

Este fin de semana me tomé el tiempo de organizar algunas fotografías que había tomado hace un tiempo, desafortunadamente la organización era un tanto caótica y difícil de navegar. Porque tenía muchas subcarpetas, así que en lugar de navegar de una en una, cortar los archivos, entrar a la siguiente y mover los archivos nuevamente, lo arreglé en un par de minutos con la Terminal. Veamos cómo se hace.
---

## Escenario

Tenía una serie de carpetas parecido a esto:

```
2020/
    01-Enero/
        Semana1/
            img_0000.cr2
            img_0001.cr2
        Semana2/
            img_0002.cr2
            img_0003.cr2
        Semana3/
            img_0004.cr2
            img_0005.cr2
        Semana3/
            img_0006.cr2
            img_0007.cr2
            img_0008.cr2

```

Y quería dejarla de esta forma:

```
2020/
    01-Enero/
            img_0000.cr2
            img_0001.cr2
            img_0002.cr2
            img_0003.cr2
            img_0004.cr2
            img_0005.cr2
            img_0006.cr2
            img_0007.cr2
            img_0008.cr2

```

Repetir este proceso durante carpetas correspondientes a los meses y a varios años era simplemente ridículo, así que tomé la idea que habíamos planteado para *[Mover archivos de subcarpetas a toda velocidad](https://andriuzha.github.io/2025-12-19-moviendo-archivos-de-subcarpetas-toda-velocidad-linux)* y hacer unos cuantos cambios, veamos cómo:

## Consideraciones

Lo primero que debieras hacer es entrar a la carpeta en la que quieres buscar los archivos, esto se hace con:

```bash
cd /carpeta/archivos/desordenados

```

Una vez dentro de la carpeta ejecutamos el comando:

```bash
find . -name '*.cr2' -print0 | xargs -0 sh -c 'for file; do mv "$file" "${file%/*}"/..; done' sh

```

Como vemos es muy parecida a la solución anterior de mover archivos, en este caso el `sh` al final permite la iteración de los argumentos de `xargs`.

Por supuesto deberás cambiar la extensión `*.cr2` por aquella que sea de tu interés.

Por último, si quieres borrar las carpetas vacías, puedes utilizar:

```bash
find . -type d -empty -print -delete

```

