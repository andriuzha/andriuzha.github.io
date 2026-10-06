---
layout: post
title: Evita la creación de archivos .DS_Store en unidades externas
description: Desactiva la creación automática de archivos ocultos .DS_Store en discos y unidades USB en macOS.
summary: Explicación y comandos para evitar que macOS cree archivos .DS_Store en unidades externas y cómo revertir el cambio.
comments: true
tags: [Mac, Tutoriales]
---

Ya en un [anterior post] (https://andriuzha.github.io/2026/01/13/archivos-ds-store-y-comenzar-desde-ceros) explicábamos qué son los archivos `.DS_Store`, su función en OS X y cómo realizar una purga de los mismos. Resumiendo, el comportamiento de estos archivos son pequeñas instrucciones de preferencias que genera el sistema.

Cuando copiamos archivos de una Mac a otra, esto es una gran ventaja, ya que nos permite mantener la estructura actual de esa carpeta; así, las preferencias como vista o el orden en el que se muestran los archivos se mantienen. Esto es especialmente útil en copias de respaldo. El problema surge cuando pasamos estos archivos a un sistema "no Mac": si copiamos archivos y estos se ven en una PC con Windows o en un teléfono Android, por ejemplo, veremos las carpetas que hemos pasado con un montón de archivos `.DS_Store` que mantienen la misma ruta que las carpetas. Con el resultado frecuente que suele ser molesto o hasta desesperante. Vamos a solucionarlo.

Abrimos una Terminal, ubicada en **Aplicaciones > Utilidades**. Ahora copiamos y pegamos el siguiente comando para evitar la creación de estos archivos en unidades USB (memorias flash, discos duros externos, teléfonos inteligentes, etc.):

```bash
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool false

```

Si por alguna razón queremos que OS X vuelva a generar los archivos `.DS_Store`, el comando es el siguiente:

```bash
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true

```

Para que los cambios sean efectivos necesitamos reiniciar el Finder con:

```bash
killall Finder

```
Escrito originalmente el 03/02/2016
