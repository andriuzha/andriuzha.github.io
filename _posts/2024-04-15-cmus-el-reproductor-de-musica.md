---
layout: post
title: CMUS El reproductor de música minimalista para la terminal
description: Aprende a instalar y utilizar CMUS, un reproductor de audio ultraligero y basado en texto para Linux y macOS.
summary: Guía básica de instalación y comandos principales para CMUS, el reproductor de música minimalista basado en terminal.
comments: true
tags: [Linux, Mac]
---

CMUS (C Music Player) es un reproductor de audio ligero, apenas unos 20 Mb en RAM, basado en texto para sistemas operativos tipo Unix. Su interfaz minimalista hace que su punto fuerte sea la eficiencia. Este reproductor funciona exclusivamente a través de comandos de teclado, lo que lo convierte en una opción ideal para usuarios que buscan una experiencia de reproducción de música sin distracciones.

## Instalación

La instalación es muy simple, ya que está en la mayoría de los repositorios oficiales, ahora estoy en Debian (y para sus derivadas) es con el siguiente comando:

```bash
apt install cmus

```

Recuerda colocar el manejador de paquetes de tu distribución.  
También está para Mac mediante MacPorts o Homebrew, y siempre lo puedes compilar desde su código fuente: [https://github.com/cmus/cmus](https://github.com/cmus/cmus).

## Comandos básicos

Aquí hay una guía básica de comandos para poder iniciarte:

| Comando | Función |
| --- | --- |
| ↑/↓ | Moverse por la lista de canciones |
| TAB | Cambiar entre vistas (biblioteca, lista de reproducción, cola, etc.) |
| / | Buscar por nombre de canción |
| q | Salir de CMUS |
| Espacio | Reproducir/Pausar |
| Enter | Seleccionar y reproducir |
| z | Detener |
| f | Avanzar a la siguiente canción |
| b | Retroceder a la canción anterior |
| m | Silenciar/Desactivar silencio |
| v | Ajustar volumen |
| n | Crear nueva lista de reproducción |
| o | Abrir lista de reproducción |
| a | Agregar canción a la lista de reproducción actual |
| d | Eliminar canción de la lista de reproducción actual |
| i | Agregar canción a la cola |
| r | Eliminar canción de la cola |
| x | Vaciar la cola |
| c | Mostrar información de la canción actual |
| l | Mostrar lista de canciones en reproducción |
| t | Mostrar información del tiempo de reproducción |
| h | Mostrar ayuda |

Esta es una excelente opción si buscas un reproductor de música ligero, eficiente y minimalista. Al estar basado en una interfaz por texto y sus comandos por teclado lo convierten en una alternativa perfecta para los que valoramos la simplicidad y la productividad.

