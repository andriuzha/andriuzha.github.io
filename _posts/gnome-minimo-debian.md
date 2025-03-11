---
layout: post
title: Instala gnome mínimo en Debian
description: Instrucciones para instalar Gnome en Debian
summary: Guía de instalación de varias versiones de Gnome en Debian, 
comments: true
tags: [Linux, Tutoriales]
---

Este es un pequeño tutorial de como instalar versiones mínimas de Gnome en Debian, esto significa instalarlo sin LibreOffice, sin la Tienda de aplicaciones, los reproductores multimedia, juegos, Mapas y muchas otras aplicaciones que posiblemente no queremos, no es que sean malas, al contrario, todas ellas son de excelente calidad, pero tenemos la libertad de decidir si queremos o no tenerlas en nuestro sistema. Bien, ahora, existen 3 métodos con diferentes resultados.

**Requisitos**

Partimos de una instalación mínima de Debian, únicamente con la terminal. Primero ascendemos a root y actualizamos la listas de paquetes de los repositorios: 

`su - apt update`

**Método 0**  
Es importante que no iniciemos el comando tasksel, debido a que esta interfaz, si nos proporcionará Gnome, pero junto a todas las demás aplicaciones, que precisamente no queremos instalar.   

Ahora veamos los tres métodos que he probado:

**Método 1**  
Instalamos el metapaquete de Gnome básico:  

`apt install gnome-core`

Muy sencillo. Esto terminará instalando Gnome con: 
*Gestor de inicio de sesión, Archivos, Firefox, Tienda de Software, Editor de texto, Contactos, Extensiones, Videos, Calculadora, Configuración, Monitor del sistema, Terminal, Analizador de discos, Discos, Visor de imágenes, Visor de documentos, Tipografías*  

**Método 2**  
Procedemos a instalar los paquetes necesarios:  

`apt install gnome-applets gnome-backgrounds gnome-control-center gnome-session gnome-shell gnome-terminal gjs mutter`

Tendremos Gnome con: 
*Gestor de inicio de sesión, Archivos, Ayuda, Configuración, Configuración de Red, Controles parentales, Estadísticas de uso, Extensiones, Monitor de sistema y Terminal.*

**Método 3**  
Instalamos únicamente dos paquetes: 

`apt install gnome-shell gnome-terminal`

Al terminar la instalación, será necesario dar de alta el servicio de inicio de sesión de Gnome y después arrancarlo, lo hacemos a través de los comandos: 

`systemctl enable gdm.service   
systemctl start gdm.service`

Tendremos Gnome únicamente con: 
*Gestor de inicio de sesión, Ayuda, Configuración, Extensiones, Terminal*  

A partir de este punto tendrás que instalar manualmente todas las aplicaciones que necesites a través de la Terminal.
