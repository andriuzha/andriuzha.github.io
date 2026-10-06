---
layout: post
title: Convirtiendo miles de imágenes en Linux
description: Aprende a convertir lotes masivos de imágenes en Linux usando la terminal y herramientas como ImageMagick o mogrify de forma eficiente.
summary: Guía práctica para procesar y convertir miles de imágenes simultáneamente en Linux utilizando comandos de terminal y optimizando tiempo de ejecución.
comments: true
tags: [Linux, Tutoriales]
---

Procesar y convertir formatos de imágenes uno por uno desde una interfaz gráfica puede convertirse en una tarea interminable cuando nos enfrentamos a cientos o miles de archivos. Afortunadamente, la terminal de Linux nos ofrece herramientas extraordinariamente potentes para automatizar y acelerar este proceso en cuestión de segundos o minutos.

## Requisitos previos

Para realizar conversiones masivas de formato, compresión o escalado, la herramienta por excelencia en Linux es **ImageMagick**. Puedes instalarla en la mayoría de distribuciones con el gestor de paquetes correspondiente:

En Debian/Ubuntu y derivados:

```bash
apt install imagemagick

```


## Convertir un lote de imágenes

La forma más directa de convertir múltiples imágenes manteniendo las originales es utilizar un bucle `for` en Bash o emplear el comando `mogrify`.

### Método 1: Uso de bucle `for` (Recomendado)

Este método te permite tener control total sobre el nombre de salida y conserva los archivos originales en su formato de origen:

```bash
for img in *.png; do
    convert "$img" "${img%.png}.jpg"
done

```

### Método 2: Uso de `mogrify` para conversión rápida

Si deseas procesar un directorio completo y convertir el formato en lote:

```bash
mogrify -format jpg *.png

```

> **Nota:** `mogrify` sobrescribirá o creará archivos en el mismo directorio. Si realizas transformaciones sobre la misma extensión, asegúrate de hacer una copia de seguridad previa.

## Procesamiento paralelo para miles de archivos

Cuando se trata de miles de imágenes, un bucle tradicional secuencial solo utiliza un núcleo del procesador. Para aprovechar todos los núcleos de tu CPU y reducir el tiempo de espera drásticamente, podemos combinar `find` con `xargs` o `parallel`:

```bash
find . -type f -name '*.png' -print0 | xargs -0 -P $(nproc) -I {} sh -c 'convert "$1" "${1%.png}.jpg"' _ {}

```

Donde `-P $(nproc)` detecta automáticamente el número de núcleos disponibles en tu procesador para ejecutar las conversiones en paralelo.

## Optimización y limpieza

Una vez completada la conversión, puedes verificar los resultados y, si lo deseas, remover los archivos antiguos del formato original:

```bash
find . -type f -name '*.png' -delete

```
