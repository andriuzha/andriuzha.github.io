---
layout: post
title: Realiza descargas de tu servidor desde el terminal
description: Aprende a realizar copias de seguridad y descargas desde tu servidor remoto utilizando Rsync a través de SSH.
summary: Guía explicativa sobre las ventajas de usar Rsync frente a FTP para realizar sincronizaciones y respaldos eficientes desde la terminal.
comments: true
tags: [Linux, Mac, Tutoriales]
---

Hace poco veíamos cómo [descargar archivos desde nuestro servidor mediante FTP con la terminal.](https://andriuzha.github.io/2024/12/15/realiza-descargas-de-tu-servidor-desde-el-terminal) Veremos como hacerlo mediante Rsync.

## Aclaremos un par de cosas primero

FTP es un protocolo estandar que nos permite transferir por red. Es fácil de configurar y es muy robusto, por otro lado rsync es un protocolo de copias y sincronización. La pregunta es porqué deberíamos utilizar uno u otro.

FTP puede ser útil si solo vas a utilizar para descargar un archivo de respaldo que ya tengas en tu servidor o si deseas subir el sitio web que ya tienes en local, pero es poco eficiente cuando añades cambios constantemente ya que tendías que subir y reemplazar todo nuevamente o revisar cada archivo que cambiaste para poderlo reemplazar, cuando son muchos archivos en muchas carpetas el proceso es tormentoso, Rsync en este caso es nuestra herramienta a considerar.

La primera ventaja de realizar las copias con este método sobre FTP, es que sincronizará únicamente los archivos que se hayan modificado desde la última copia, evitando así tener que volver a descargar, cientos de MB o incluso gigas. La segunda es la herramienta es recursiva, especialmente útil cuando se trabaja con muchos directorios y la última es que si necesitas interrumpir la operación por algún motivo, Rsync retomará la copia justo donde se quedo, evitando tener que empezar nuevamente.

## Entendiendo Rsync

El funcionamiento de rsync es muy simple:

```bash
rsync -opciones carpeta/origen carpeta/destino

```

Para poder realizar una copia de seguridad del servidor remoto a una carpeta en mi maquina local es necesario tener acceso al ssh mediante la terminal. Esta operación se le denomina "poll"

Utilizó la siguiente configuración para realizar las descargas:

```bash
rsync -avzP usuario@123.456.789.000:/carpeta/remota ~/backup/servidor/

```

## Vamos por pasos

* **`rsync`**: Es el comando que realiza las copias.
* **`-avzP`**: Estas opciones son:
* **a**: mantiene los enlaces simbólicos, conserva las propiedades de los archivos como la hora y los permisos, sincroniza de forma recursiva.
* **z**: comprime los archivos y alivia la carga de la red.
* **v**: muestra el proceso de la copia.
* **P**: ayuda a mostrar la información de v en un formato para humanos y permite reanudar descargas.


* **`usuario@123.456.789.000:/carpeta_remota`**: Es la forma en como conectas mediante SSH, observa que al final de la dirección del servidor esta un **`:`** indica que a partir de ahí va a buscar dentro del servidor los archivos o carpetas a sincronizar, si deseas realizar un respaldo de todo el servidor, solo manten `:/`.
* **`~/backup/`**: Es la carpeta donde se guardarán los archivos.

Ahora estas listo para realizar respaldos de una forma más eficiente.

