---
layout: post
title: Descarga archivos FTP desde el terminal
description: Aprende a descargar archivos y directorios de forma recursiva desde un servidor FTP utilizando wget desde la terminal en Linux y macOS.
summary: Guía práctica para realizar respaldos eficientes desde servidores FTP usando wget con opciones de usuario, contraseña y descarga recursiva.
comments: true
tags: [Linux, Mac, Tutoriales]
---

Esta semana tengo que realizar el respaldo de mi servidor, son muchos GB como para descargar archivo por archivo y aunque existen programas dedicados especialmente a ello, como FileZilla o Cyberduck, veamos como hacerlo un poco más rápido, más sencillo, con descarga recursiva y desde la terminal.

## Requisitos

Para esto necesitaremos obviamente tener acceso al servidor, es decir un usuario, la contraseña y tener identificada la ruta de los archivos que queremos descargar. También haremos uso de la herramienta `wget` que entre muchas cosas nos sirve para recuperar archivos en línea y duplicar sitios web. Lo instalamos mediante:

```bash
apt install wget

```

`apt` es el gestor de paquetes de Debian, deberás de utilizar aquella que corresponda a tu distribución. Si estas en macOS puedes hacerlo mediante [brew](https://brew.sh/) o [MacPorts](https://www.macports.org/).

## Preparando la descarga

En este caso voy a crear una carpeta en el directorio de descargas, entrar en ella y ahí crear una carpeta llamada `backupServer`, para nuevamente ingresar en ella, de forma que quedaría `~/Downloads/backupServer`.

Para ello continuemos dentro de la terminal y colocamos:

```bash
cd Downloads
mkdir backupServer
cd backupServer

```

## Descargando

Ya que estamos dentro de la carpeta donde guardaremos los archivos debemos de mantener la siguiente estructura:

```bash
wget -r --user=user@email.xyz --password=P4SSW0RD# ftp://68.70.164.21:21/rutadearchivos/

```

## Desglosando

* **`wget -r`**: Indica que se utilice la herramienta de descarga de forma recursiva.
* **`--user=user@email.xyz`**: Aquí colocaremos el usuario (es posible que se requiera de un formato tipo email).
* **`--password=P4SSW0RD#`**: Colocaremos nuestra contraseña.
* **`ftp://123.456.78.90`**: Los números del 1 al 0 indican la ruta de ftp, también puede ser que se encuentre en forma de una url como `ftp://miservidor.xyz`.
* **`:21`**: Es el puerto por defecto donde se conecta.
* **`/rutadearchivos/`**: Es importante conocer la ruta exacta del archivo o carpeta a descargar. Si no especificamos nada, comenzará a bajar todos los archivos del servidor.

Esto es todo, con esto podrás ir descargando los archivos de una forma más ordenada ya que `wget` genera un registro que guarda qué archivos ya se descargaron de forma que al recuperar la lista de archivos FTP excluirá aquellos que ya estén finalizados.

