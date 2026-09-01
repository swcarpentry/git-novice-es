---
title: Creando un repositorio
teaching: 10
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Crear un repositorio local de Git.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- ¿Dónde almacena Git la información?

::::::::::::::::::::::::::::::::::::::::::::::::::

Una vez que Git está configurado,
podemos comenzar a usarlo.
Vamos a crear un directorio para nuestro trabajo y nos movemos dentro de ese directorio:

```bash
$ mkdir planets
$ cd planets
```

Después le indicamos a Git hacer de `planets` un [repository](../learners/reference.md#repositorio)— un lugar donde
Git puede almacenar las versiones de nuestros archivos:

```bash
$ git init
```

Si usamos `ls` para mostrar el contenido del directorio,
parece que nada ha cambiado:

```bash
$ ls
```

Pero si agregamos la flag `-a` para mostrar todo,
podemos ver que Git ha creado un directorio oculto dentro de `planets` llamado `.git`:

```bash
$ ls -a
```

```output
.	..	.git
```

Git utiliza este subdirectorio especial para almacenar toda la información del proyecto, incluyendo todos los archivos y subdirectorios. Si alguna vez borramos el directorio `.git`,
perderemos la historia del proyecto.

Podemos revisar que todo esté configurado correctamente
pidiendo a Git que nos informe el estado de nuestro proyecto:

```bash
$ git status
```

Si estás utilizando una versión de git distinta a la que yo utilizo, el output puede ser ligeramente distinto.

```output
# On branch master
#
# Initial commit
#
nothing to commit (create/copy files and use "git add" to track)
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Lugares para crear un repositorio Git

Ademas de rastrear la información sobre los planetas (el proyecto que ya creamos), Drácula también quiere
rastrear la información sobre las lunas. A pesar de las preocupaciones de Wolfman, Drácula crea el sub-directorio
`moons` dentro de su directorio `planets` ingresando la siguiente secuencia de comandos:

```bash
$ cd             # volver al directorio de inicio
$ mkdir planets  # crear un nuevo diretorio llamado planets
$ cd planets     # entrar al directorio planets
$ git init       # hacer del directorio planets directory un repositorio Git
$ mkdir moons    # crear un subdirectorio planets/moons
$ cd moons       # entrar al directorio planets/moons
$ git init       # hacer del subdirectorio moons un repositorio Git
```

¿Es necesario correr el comando `git init` en el sub-directorio `moons` para poder realizar el seguimiento de los archivos almacenados en este directorio?

:::::::::::::::  solution

## Solución

No. Dracula no necesita transformar el sub-directorio `moons` en un repositorio Git,
porque el repositorio `planets` realizará el seguimiento de todos los archivos,
sub-directorios y archivos de los sub-directorios dentro del directorio `planets`.
Entonces, a fin de poder hacer un seguimiento de toda la información sobre `moons`,
Dracula sólo necesita agregar el sub-directorio `moons` al directorio `planets`.

Además, los repositorios Git pueden interferir entre sí si están "anidados" dentro de
otro directorio: el repositorio exterior intentará controlar la versión
del repositorio interno. Por lo tanto, lo mejor es crear cada nuevo repositorio Git
en un directorio separado. Para asegurarte que no hay un repositorio en conflicto
en el directorio, revisa el output de `git status`. Si se parece a
lo siguiente, podrás crear un nuevo  repositorio como se ha mostrado
arriba:

```bash
$ git status
```

```output
fatal: Not a git repository (or any of the parent directories): .git
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Corrigiendo errores de `git init`

Wolfman le explica a Dracula cómo un repositorio anidado es redudante y puede causar problemas ms adelante.
Dracula quiere eliminar el repositorio anidado. Cómo puede Dracula deshacer el último `git init` en el sub-directorio `moons`?

:::::::::::::::  solution

## Solución - USAR CON CUIDADO!

Para deshacerse de este pequeño error, Dracula puede simplemente eliminar el directorio `.git`
del subdirectorio `moons`. Para ello puede ejecutar el siguiente comando desde el interior del directorio `moons`:

```bash
$ rm -rf moons/.git
```

¡Pero ten cuidado! Ejecutar este comando en el directorio incorrecto eliminará
toda la historia git de un proyecto que podrías querer conservar.
Por lo tanto, revisa siempre tu directorio actual usando el comando `pwd`.



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::



:::::::::::::::::::::::::::::::::::::::: keypoints

- `git init` inicializa un repositorio.

::::::::::::::::::::::::::::::::::::::::::::::::::


