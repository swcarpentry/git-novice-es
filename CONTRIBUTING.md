# Contribuyendo

[Software Carpentry][swc-site] y [Data Carpentry][dc-site] son ​
proyectos de código abierto, y damos la bienvenida a contribuciones 
de todo tipo: nuevas lecciones, correcciones al material existente, 
informes de errores, y revisiones de cambios propuestos son todas
bienvenidas.

## Acuerdo de Colaboración

Al contribuir, aceptas que podemos redistribuir tu trabajo bajo
[nuestra licencia](LICENCIA.md). A cambio, abordaremos tus problemas 
y/o evaluaremos tu propuesta de cambio tan pronto como podamos, y 
te ayudaremos a convertirte en miembro de nuestra comunidad. Todos los 
involucrados en [Software Carpentry][swc-site] y 
[Data Carpentry][dc-site]
aceptan cumplir con nuestro [código de conducta](CONDUCT.md).

## Cómo contribuir

La forma más fácil de comenzar es presentar un problema para 
poder corregirlo, como un error ortográfico, algunas palabras no claras,
o un error fáctico. Contribuir es una buena forma de presentarte 
y conocer a algunos de los miembros de nuestra comunidad.

1. Si no tienes una cuenta de [GitHub][github], puedes [enviarnos comentarios por correo electrónico][contacto]. Sin embargo, podremos responder más rápidamente si usas uno de los otros métodos descritos a continuación.

2. Si tienes una cuenta de[GitHub][github], o estás dispuesto a [crear una][github-join], pero no sabes como usar git, puedes informar de problemas o sugerir mejoras al [crear un problema o **issue**][nuevo-problema]. Esto nos permite asignar la tarea a alguien y responderle en un hilo de discusión.

3. Si te sientes cómodo con Git, y te gustaría agregar o cambiar material, puedes enviar una solicitud de inclusión o **pull request** (PR). Las  instrucciones para hacerlo [se incluyen a continuación](#using-github).

## Donde Contribuir

1. Si deseas cambiar esta lección, por favor trabaja en <https://github.com/swcarpentry/git-novice-es>, que se puede ver en <https://swcarpentry.github.io/git-novice-es>.

2. Si deseas cambiar la lección de ejemplo, por favor trabaja en <https://github.com/carpentries/lesson-example>, que documenta el formato de nuestras lecciones y se puede ver en <https://carpentries.github.io/lesson-example>.

3. Si deseas cambiar la plantilla utilizada para los sitios web del taller, por favor trabaja en <https://github.com/carpentries/workshop-template>. La página de inicio de ese repositorio explica cómo configurar los sitios web de los talleres, mientras que las páginas adicionales en <https://carpentries.github.io/workshop-template> proporcionan más información sobre nuestros criterios de diseño.

4. Si deseas cambiar los archivos de estilo CSS, herramientas, o texto estándar HTML para lecciones o talleres almacenados en `_includes` o` _layouts`, por favor trabaja en <https://github.com/carpentries/styles>.

## Qué aportar

Hay muchas maneras de contribuir, desde escribir nuevos ejercicios y
mejorar los existentes hasta actualizar o completar la documentación y
enviando [informes de error o **issues**][nuevo-problema] sobre cosas que no
funcionan, no son claras o faltan. Si estás buscando ideas, por favor
revisa [la lista de problemas para este repositorio][issues], o la de los 
problemas de los proyectos [Data Carpentry][dc-issues] y 
[Software Carpentry][swc-issues].

Los comentarios sobre problemas y revisiones de solicitudes de
inclusión son igualmente bienvenidos: somos más inteligentes juntos
que por nuestra cuenta. Los comentarios de principiantes y recién 
llegados son particularmente valiosos: es fácil para las personas
que han estado usando estas lecciones por un tiempo, olvidar lo 
impenetrable que puede ser parte de este material, por lo que los 
ojos frescos son siempre bienvenidos.

## Qué *No* contribuir

Nuestras lecciones ya contienen más material de lo que podemos cubrir
en un taller típico, por lo que usualmente *no* buscamos más 
conceptos o herramientas para agregarles. Como regla general, si quieres
presentar una nueva idea, debes (a) estimar cuánto tiempo tomará 
enseñarla y (b) explicar lo que sacarías para darle espacio. El primero
anima a los contribuyentes a ser honestos acerca de los requisitos;
el segundo, pensar bien las prioridades.

Tampoco buscamos ejercicios u otro material que sólo se ejecute en 
una plataforma. Nuestros talleres suelen contener una mezcla de 
usuarios de Windows, Mac OS X y Linux; para ser utilizable, nuestras 
lecciones deben correr igualmente bien en las tres plataformas.

## Usando GitHub

Si eliges contribuir a través de GitHub, es posible que desees mirar
[Cómo contribuir a un proyecto de código abierto en GitHub][cómo-contribuir].

En resumen:

1. La copia publicada de la lección está en la rama `gh-pages` del repositorio (para que GitHub la regenere automáticamente). Por favor crea todas las ramas de eso, y fusiona la rama `gh-pages` del [repositorio maestro][repo] en la rama` gh-pages` antes de comenzar a trabajar. Por favor, *no* trabajes directamente en su rama `gh-pages`, ya que eso te dificultará trabajar en otras contribuciones.

2. Usamos [GitHub flow] [github-flow] para gestionar los cambios:
   1. Crea una nueva rama en tu copia de escritorio de este repositorio para cada cambio significativo.
   2. Confirma (**commit**) el cambio en esa rama.
   3. Empuja esa rama a su tenedor de este repositorio en GitHub.
   4. Envía una solicitud de inserción (**pull request**) desde esa rama al [repositorio principal] [repo].
   5. Si recibe comentarios,
      haz cambios en tu escritorio y envíalos (**push**) a tu rama en GitHub:
      la solicitud de inserción se actualizará automáticamente.

Cada lección tiene dos mantenedores que revisan problemas y solicitudes 
inserción o animan a otros a hacerlos. Los mantenedores son 
voluntarios de la comunidad, y tener la última palabra sobre lo que 
se incluye en la lección.

## Otros recursos

La discusión general de [Software Carpentry][swc-site] y 
[Data Carpentry][dc-site] ocurre en la 
[lista de distribución de discusiones][lista-de-discusión], 
a la cual todos son bienvenidos. También puedes 
[contactarnos por correo electrónico][contacto].

[contacto]: mailto:admin@software-carpentry.org
[dc-issues]: https://github.com/issues?q=user%3Adatacarpentry
[dc-lessons]: http://datacarpentry.org/lessons/
[dc-site]: http://datacarpentry.org/
[lista-de-discusión]: http://lists.software-carpentry.org/listinfo/discuss
[github]: http://github.com
[github-flow]: https://guides.github.com/introduction/flow/
[github-join]: https://github.com/join
[cómo-contribuir]: https://egghead.io/series/how-to-contribute-to-an-open-source-project-on-github
[nuevo-problema]: https://github.com/swcarpentry/git-novice/issues/new
[issues]: https://github.com/swcarpentry/git-novice/issues/
[repo]: https://github.com/swcarpentry/git-novice/
[swc-issues]: https://github.com/issues?q=user%3Aswcarpentry
[swc-lessons]: http://software-carpentry.org/lessons/
[swc-site]: http://software-carpentry.org/
