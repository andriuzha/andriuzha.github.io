---
layout: post
title: Archivos .DS_Store y comenzar desde ceros
description: Aprende a buscar y eliminar los archivos ocultos .DS_Store en macOS para solucionar problemas de personalización.
summary: Guía paso a paso para purgar los archivos .DS_Store del disco duro usando la Terminal y reiniciar el Finder para empezar desde cero.
comments: true
tags: [Mac, Tutoriales]
---

OS X ocupa los archivos `.DS_Store` (una abreviatura de *Desktop Services Store*) para almacenar atributos específicos de todas y cada una de las carpetas, como la posición de iconos o fondos de pantalla personalizados. El Finder se encarga de crear estos archivos, al comenzar su nombre por un punto nos indica que es un archivo oculto.

Este pequeño archivo nos facilita en gran medida mantener cierto orden al crear, por ejemplo, copias de seguridad, ya que estas copias incluirán este archivo y el orden o el modo de visualización de los archivos se respetará. Sin embargo, la posible sobrepersonalización de las carpetas puede acabar generando problemas y más confusión que organización. Es por eso que aprenderemos a cómo purgar todos estos archivos del disco duro y comenzar desde ceros.

Lo que haremos será una búsqueda asociada a estos archivos para después eliminarlos. Es importante para esta acción no tener conectado el disco de copia de Time Machine, ya que generaría mucho mayor tiempo en la búsqueda de los `.DS_Store`.

Abrimos la Terminal, copiamos y pegamos lo siguiente:

```bash
sudo find /carpeta/archivos/ -name .DS_Store -exec rm -fv {} +

```

Entendamos qué estamos haciendo:

* `sudo` es el comando que nos otorga acceso temporal a los privilegios de root.
* `find` es el comando para encontrar archivos y a continuación se le indica dónde debe buscar.
* `-name` señala el nombre, en este caso `.DS_Store`.
* `-exec rm` la primera parte indica que una vez que `find` encontró el archivo llame a otro comando, en este caso `rm` que es el de borrar; `-fv` es para forzar el borrado (`f`) y para mostrarnos en pantalla información sobre la operación (`v`), respectivamente; por último `{}` indica que se trabaje con el archivo que `find` encontró y `+` finaliza el proceso de `-exec`.

Este proceso te mostrará el borrado de todas las coincidencias. Ya por último, nos queda reiniciar el launcher para que genere los `.DS_Store` nuevamente:

```bash
killall Finder

```

Escrito originalmente: 13/01/2016
