---
layout: post
title: Crea una lista de archivos de una carpeta
description: Aprende a crear un inventario con los nombres de tus archivos en Mac y Linux fácilmente.
summary: Guía paso a paso para obtener el listado de archivos de una carpeta en macOS y Linux mediante TextEdit o la Terminal.
comments: true
tags: [Linux, Mac, Tutoriales]
---

En esta semana tuve que realizar un inventario de muchos archivos que había dentro de algunas carpetas de un disco duro externo. Como es muy tedioso andar escribiendo nombre por nombre o dando click sobre el archivo para que nos de la opción de renombrarlo, a continuación copiar el nombre y pegarlo en un documento, hagamos las cosas más simples.

Hay dos posibles soluciones, una de ella es seleccionar todos los archivos y copiarlos, esto nos permitirá pegarlos dentro de cualquier contenedor que los acepte, otra ubicación en un disco duro, usb, el gestor de email, pero ¿qué pasa sí el contenedor no acepta los archivos? Simplemente procederá a colocar el nombre de los archivos. así que abriremos TextEdit, pero sí pegamos directamente sobre él veremos que se se pegan las miniaturas de los archivos, lo cual no nos sirve de nada, así que pulsamos `⌘` + `⇧` + `T` esto cambiara el formato de texto enriquecido a texto plano, ahora sí, podemos pegar los nombres y veremos que los nombres de los archivos se listan.

Podemos dar un paso adelante y automatizar esta tarea, que también sirve para Linux, para ello debemos de recurrir al Terminal, dentro de el ponemos el siguiente comando

```bash
ls Ruta/de/origen > Ruta/de/destino/archivo.txt

```

Como seguramente ya sabes, puedes escribir la primera parte del comando, arrastrar la carpeta para que el terminal tenga la ruta escribir la parte siguiente del terminal, arrastrar la carpeta de destino y escribir el nombre del archivo de nuestro listado. Por ejemplo:

```bash
ls /carpeta/MilesdeArchivos/ > Desktop/lista.txt

```

Listará los archivos que hay en la carpeta "Miles de Archivos" y los guardará en el escritorio con el nombre de lista, ahorrándonos un montón de tiempo.

Escrito originalmente: 13/04/2016

