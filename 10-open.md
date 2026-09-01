---
title: La ciencia abierta
teaching: 5
exercises: 5
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explica como el control de versiones nos ayuda a tener un cuaderno electrónico para todo nuestro trabajo computacional.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- ¿Cómo un control de versiones me puede ayudar a tener mi trabajo más abierto?

::::::::::::::::::::::::::::::::::::::::::::::::::

> Lo opuesto a "abierto" no es "cerrado".
> Lo opuesto a "abierto" es "quebrado".
> 
> \--- John Wilbanks

El libre intercambio de información podría ser el ideal en Ciencia. Pero la realidad, a menudo, es mucho más complicada.
En la práctica cotidiana vemos situaciones como la siguiente:

- Una científica recoge algunos datos y los almacena en una máquina que seguramente tiene en su oficina.
- Luego ella escribe y modifica unos pocos programas para analizar los datos (los cuales residen en su computadora).
- Una vez que tiene algunos resultados, ella escribe y presenta su artículo. Podría incluir sus datos -en varias revistas que los requieran- pero probablemente no incluya su código.
- El tiempo pasa.
- La revista envía las revisiones de un puñado de personas anónimas que trabajan en su campo de actividad.
  Ella revisa su artículo para satisfacer las revisiones propuestas. Durante ese tiempo ella también podría modificar los **scripts** que escribió anteriormente, y vuelve a enviar.
- Pasa más tiempo.
- El artículo finalmente se publica.
- Se podría incluir un enlace a una copia online de sus datos, pero el mismo artículo está detrás de un sitio web de pago: sólo las personas que tienen acceso personal o institucional serán capaces de leerlo.

Para muchos otros científicos, el proceso abierto se ve así:

- Los datos que obtiene son almacenados, tan pronto como los colecta, en un repositorio de acceso abierto, como puede ser [figshare](https://figshare.com/) o [Zenodo](https://zenodo.org), obteniendo su propio [Digital Object Identifier] ([https://en.wikipedia.org/wiki/Digital\_object\_identifier](https://en.wikipedia.org/wiki/Digital_object_identifier)) (DOI). O los datos que han sido recientemente publicados, son almacenados en [Dryad](https://datadryad.org/).
- La científica crea un nuevo repositorio en GitHub para guardar su trabajo.
- Al hacer su análisis de los datos, guarda los cambios de sus **scripts** (y posiblemente algunos archivos de salida) en ese repositorio. También utiliza el repositorio para su artículo. Entonces ese repositorio es el centro de colaboración con sus colegas.
- Cuando está satisfecha con el estado de su artículo, publica una versión en [arXiv](https://arxiv.org/) o en algún otro servidor de preimpresión para invitar a sus compañeros a una retroalimentación.
- Basado en esa retroalimentación, puede escribir varias revisiones antes de enviar finalmente su artículo a la revista.
- El artículo publicado incluye enlaces a su preimpresión y a sus repositorios de código y datos, lo que hace mucho más fácil para otros científicos utilizar este trabajo como punto de partida para su propia investigación.

Este modelo abierto acelera la investigación: el trabajo abierto [se cita y se reutiliza](https://dx.doi.org/10.1371/journal.pone.0000308). Sin embargo, las personas que quieren trabajar de esta manera necesitan tomar algunas decisiones sobre qué significa exactamente "abierto" y cómo hacerlo. Puedes encontrar más información sobre los diferentes aspectos de la Ciencia Abierta en [el libro](https://link.springer.com/book/10.1007/978-3-319-00026-8).

Ésta es una de las muchas razones por las que enseñamos el control de versiones. Cuando se utiliza con diligencia, responde a "cómo" actúa un cuaderno electrónico compartible:

- Las etapas conceptuales del trabajo están documentadas, incluyendo quién hizo qué y cuándo se hizo. Cada paso está marcado con un identificador (el ID de confirmación) de cada uno de los intentos y propósitos.
- Puedes vincular tu documentación de ideas y otros trabajos intelectuales directamente con los cambios que surgen de ellos.
- Puedes referirte a lo que utilizaste en tu investigación para obtener tus resultados computacionales de manera única y recuperable.
- Con un sistema de control de versiones como Git, todo el historial del repositorio es fácil de archivar para siempre.

:::::::::::::::::::::::::::::::::::::::::  callout

## Haciendo código citable

[Esta breve guía](https://guides.github.com/activities/citable-code/) de GitHub
explica cómo crear un "Digital Object Identifier (DOI)" para tu código, tus artículos, o cualquier cosa alojada en un repositorio de control de versiones.


::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## ¿Cuán reproducible es mi trabajo?

Pide a un compañero de laboratorio que reproduzca un resultado que obtuviste
utilizando sólo lo que está disponible en un documento publicado o en la web.
Luego, trata de hacer lo mismo con los resultados de tu labmate.
Finalmente, reproducir los resultados de otro laboratorio.


::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## ¿Cómo encontrar un repositorio de datos adecuado?

Navega por Internet durante un par de minutos y echa un vistazo a los repositorios de datos mencionado anteriormente: [Figshare](https://figshare.com/), [Zenodo](https://zenodo.org), [Dryad](https://datadryad.org/). Dependiendo de tu campo de investigación, encuentra repositorios reconocidos por la comunidad en tu campo. También puede ser útil [estos repositorios de datos recomendados por Nature](https://www.nature.com/sdata/data-policies/repositories). Discute con tu vecino qué repositorio de datos deseas abordar para tu proyecto actual y explicale por qué.


::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## ¿Puedo publicar código también?

Hay nuevas maneras de publicar código y hacer que sea citable. Uno de ellos se describe [en la página principal del mismo GitHub](https://guides.github.com/activities/citable-code/). Básicamente es una combinación de GitHub (donde está el código) y Zenodo (el repositorio que crea el DOI). Lee esta página mientras sabes que ésta es sólo una de las muchas maneras de hacer tu código citable.


::::::::::::::::::::::::::::::::::::::::::::::::::



:::::::::::::::::::::::::::::::::::::::: keypoints

- Trabajo científico abierto es más útil y puede ser citado más que si no lo es.

::::::::::::::::::::::::::::::::::::::::::::::::::


