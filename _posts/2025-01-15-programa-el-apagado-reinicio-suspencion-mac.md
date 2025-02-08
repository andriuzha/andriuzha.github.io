---
layout: post
title: Programa el apagado, reinicio o suspención de tu Mac
description: Programando el apagado, reinicio o suspención de tu Mac
summary: Aprende a programar el apagado, reinicio o suspención de tu computadora en MacOS 
comments: true
tags: [tutorial, mac] 
---

Todos tenemos ocasiones en las cuales, por algún motivo, tenemos que dejar nuestra Mac trabajando un determinado tiempo pero no podemos estar delante de la máquina para que al teminar dicha tarea, esta se apague. Pongamps un ejemplo: trabajamos con vídeos, y muchas veces necesito transcodificar archivos que tardan 4, 5 horas o más, así que muchas veces en lugar de despertar cada 2 horas por la noche (o tener que regresar a la oficina) para ver sí ya termino y para apagarla, vamos a solucionar el problema programando el apagado. 

El programado se hace realmente fácil, a través del terminal con la instrucción es shutdown, pero dado que este es una instrucción que se ejecuta como super usuario, pedirá tu contraseña de usuario, además de eso debemos de tener en cuenta algunas consideraciones a la hora de añadir banderas: -h now apaga el terminal de forma inmediata, sí lo que queremos es programar el apagado en un determinado tiempo lo expresaremos en minutos  -h +60 se realizará el apagado dentro de una hora. Para reiniciar, ocuparemos -r en lugar de -h. Con la bandera -s enviamos a reposo, si añadimos el tiempo de programación nos evitaremos el cambiar la configuración del Panel de Control de Energía.

Resumiendo las instrucciones:

sudo shutdown -h now (Apagar ahora)
sudo shutdown -h +60 (Apagar dentro de un tiempo determinado, expresado en minutos)

sudo shutdown –r now (Reiniciar ahora)
sudo shutdown –r +60 (Reiniciar dentro de un tiempo determinado, expresado en minutos)

sudo shutdown -s +60 (Suspender dentro de un tiempo determinado,expresado en minutos)

 Ahora no te tendrás que despertar a las 3 am para apagar tu equipo.

**Estado de ánimo:** *Etéreativo*   
**Escuchando:** *Inti Santana - La corriente ecléctica*

