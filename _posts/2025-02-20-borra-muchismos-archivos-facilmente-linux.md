---
layout: post
title: Borra carpetas con muchísimos archivos en Linux y macOS
description: Usa la terminal y el comando rm -rf para eliminar cualquier carpeta al instante. Aprende cómo y optimiza tu trabajo.
summary: Aprende a borrar carpetas rápidamente con el comando rm -rf en la terminal. Soluciona problemas de permisos con sudo y optimiza tu flujo de trabajo.
comments: true
tags: [Linux, macOS]
---

Borrar una carpeta con varios de cientos o incluso miles de archivos dentro puede ser una tarea tediosa, esto se debe a la política que aplica de los gestores de archivos, cuando vamos a borrar una carpeta con archivos dentro, o cuando la copiamos y la pegamos en otra ubicación, primero procede a contar los ítems y luego empieza la operación. Esto puede dar como resultado que sea un proceso absurdamente lento y por otra parte el proceso se interrumpirá si hay problemas con un archivo, ya sea que este corrupto o que haya problemas de permisos, etc. Vamos a solucionarlo.

Abrimos el terminal, y ahí tecleamos:

~~~
rm -rfv /ubicación/de/la/carpeta
~~~

Ahora, un truco puedes teclear únicamente el comando y arrastrar la carpeta dentro de la ventana del terminal y este se encargará de añadir la ruta de la carpeta que has arrastrado. Ya sólo queda pulsar enter para confirmar el borrado.

Debes de tener algunas consideraciones con respecto a este método: en primer lugar, este método borrará los archivos, no los enviará a la papelera, utilizaló con precaución; segundo, posiblemente quedé algún archivo que no pueda ser borrado, regularmente esto ocurre por problemas de permisos, tendrás que revisar los permisos y cambiarlos o podemos volver a solucionarlo con el terminal. Sólo debemos de agregar la instrucción de superusuario al comando, quedando así:

~~~
sudo rm -rf /ubicación/de/la/carpeta
~~~

Se te solicitará la contraseña de administrador, como es habitual.
