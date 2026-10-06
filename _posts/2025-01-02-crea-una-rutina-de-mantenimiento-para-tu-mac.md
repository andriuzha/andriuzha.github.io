---
layout: post
title: Crea una rutina de mantenimiento para tu Mac
description: Rutina básica de mantenimiento para mantener tu Mac en óptimo funcionamiento con tareas sencillas.
summary: Guía paso a paso para realizar una rutina de mantenimiento mensual en macOS, incluyendo reinicio en Modo Seguro, purga de cachés y reconstrucción de la caché compartida de carga dinámica.
comments: true
tags: [Mac, Tutoriales]
---

Cada año te lo propones y cada año fallas, realizar una rutina básica de mantenimiento tendrá a tu Mac en un buen funcionamiento. Sólo necesitas unos cuantos minutos al mes. La idea es ejecutar pequeñas tareas para que el sistema de tu mac: OS X o macOS no sufran por las tareas diarias acumuladas durante meses o años. Este mantenimiento se basa en tres tareas concretas a seguir. Siempre es una buena idea el realizarlas en un fin de semana, así, si algo se estropea, puedes repararlo durante estos días.

Veamos que tareas se necesitan:

## Reinicio en Modo Seguro

MacOs es un sistema bastante estable y no suele dar problemas, pero en ocaciones ves el sistema tarda mucho en cargar, hay cuelgues o cierres inesperados, así que vamos a ocupar este tipo de arranque para ayudar al sistema, para acceder a el sólo debemos ha hacer lo siguiente:

* Enciende tu Mac
* Justo cuando escuches el acorde de inicio (chime, sí, así se llama) pulsa la tecla ⇧
* Cuando el acorde acabe suelta la tecla.

Veras una barra indicaron muy similar a cuando tu mac se actualiza, al terminar veras que es muy similar al entorno diario, solo que algunas cosas están deshabilitadas, las transparencias, las animaciones, algunos tipos de conectividad de red podrían no funcionar, tampoco la reproducción de DVDs. Esto se debe a que cuando arrancamos la mac en modo seguro realiza algunas operaciones de limpieza y mantenimiento del sistema:

* Comprueba el volumen de inicio
* Desactiva todas las fuentes que no sean propias del sistema
* Borra la caché del sistema
* Borra la caché compartida de carga dinámica

Esto es todo lo que tendrás que realizar en este paso, solo toca reiniciar.
Ten paciencia, pues el sistema tendrá que reconstruir cachés, así que el primer reinicio puede ser un poco lento, en los posteriores volverá a su velocidad habitual, o incluso más rápido.

## Purga de cachés

Las cachés corruptas suelen ser el origen de diversos problemas en macOS, puedes ver que las aplicaciones tardan mucho en iniciar, que se quedan colgadas, o se cierran inesperadamente, la limpieza de estas suele solucionar muchos de estos problemas. Eliminarlas es seguro y fácil:

* Cerraremos todas las aplicaciones
* Abrimos Terminal que esta en Aplicaciones > Utilidades > Terminal
* Pondremos el siguiente comando:

```bash
sudo rm -rf ~/Library/Caches/

```

Cuando el proceso termine reinicia tu mac.

## Acelerando el arranque de sistema y aplicaciones

Habitualmente notas que tu Mac no va tan bien cuando tarda mucho en iniciar y en abrir aplicaciones, esto es ocasionado casi siempre por problemas con la caché dinámica compartida, este tipo de caché se encarga de precisamente evitar la realentización al abrir aplicaciones recientemente instaladas, enlazando recursos comunes en macOS, y es precisamente al dañarse estos enlaces cuando las aplicaciones tardan muchísimo en iniciar.

Para reconstruir estas cachés, abriremos el terminal y ocuparemos los siguientes comandos:

```bash
sudo update_dyld_shared_cache -debug
sudo update_dyld_shared_cache -force

```

Al tener la instrucción sudo, te solicitara la contraseña de administrador. Deberas de ocupar uno y al terminar ocupar el siguiente, al finalizar el proceso reinicia tu Mac, puede llevar unos minutos en realizar la reconstrucción, esto dependerá de la cantidad de aplicaciones instaladas y la velocidad de tu disco duro, sabrás que el proceso  termino cuando vuelvas a ver el símbolo del sistema.

Con esta simple rutina de mantenimiento, que si bien no es muy profunda, es lo suficientemente potente para mantener Mac en condiciones optimas.

Escrito originalmente: 02/01/2018
