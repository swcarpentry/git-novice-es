---
title: Ignorando cosas
teaching: 5
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Configure Git para ignorar archivos específicos.
- Explica por qué ignorar los archivos puede ser útil.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- ¿Cómo puedo indicarle a Git que ignore los archivos que no quiero rastrear?

::::::::::::::::::::::::::::::::::::::::::::::::::

¿Qué pasa si tenemos archivos que no queremos que Git rastree,
como archivos de copia de seguridad creados por nuestro editor
o archivos intermedios creados durante el análisis de datos?
Vamos a crear algunos archivos ficticios:

```bash
$ mkdir results
$ touch a.dat b.dat c.dat results/a.out results/b.out
```

Mira lo que Git dice:

```bash
$ git status
```

```output
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	a.dat
	b.dat
	c.dat
	results/
nothing added to commit but untracked files present (use "git add" to track)
```

Colocar estos archivos bajo el control de versiones sería un desperdicio de espacio en disco.
Y lo que es peor,
al tenerlos todos listados, podría distraernos de los cambios que realmente importan,
así que vamos a decirle a Git que los ignore.

Lo hacemos creando un archivo en el directorio raíz de nuestro proyecto llamado `.gitignore`:

```bash
$ nano .gitignore
$ cat .gitignore
```

```output
*.dat
results/
```

Estos patrones le dicen a Git que ignore cualquier archivo cuyo nombre termine en `.dat`
y todo lo que haya en el directorio `results`.
(Si alguno de estos archivos ya estaba siendo rastreado,
Git seguirá rastreándolos.)

Una vez que hemos creado este archivo,
la salida de `git status` es mucho más limpia:

```bash
$ git status
```

```output
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	.gitignore
nothing added to commit but untracked files present (use "git add" to track)
```

Lo único que Git advierte ahora, es el archivo `.gitignore` recién creado.
Podrías pensar que no queremos rastrearlo,
pero todos aquellos con los que compartimos nuestro repositorio probablemente desearán
ignorar las mismas cosas que nosotros.
Vamos a agregar y hacer "commit" de `.gitignore`:

```bash
$ git add .gitignore
$ git commit -m "Add the ignore file"
$ git status
```

```output
# On branch master
nothing to commit, working directory clean
```

Como ventaja, usar `.gitignore` nos ayuda a evitar agregar accidentalmente al repositorio los archivos que no queremos rastrear:

```bash
$ git add a.dat
```

```output
The following paths are ignored by one of your .gitignore files:
a.dat
Use -f if you really want to add them.
```

Si realmente queremos anular la configuración de ignorar,
podemos usar `git add -f` para obligar a Git a añadir algo. Por ejemplo,
`git add -f a.dat`.
También podemos ver siempre el estado de los archivos ignorados si queremos:

```bash
$ git status --ignored
```

```output
On branch master
Ignored files:
 (use "git add -f <file>..." to include in what will be committed)

        a.dat
        b.dat
        c.dat
        results/

nothing to commit, working directory clean
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Ignorar archivos anidados

Dado un directorio con la siguiente estructura:

```bash
results/data
results/plots
```

¿Cómo ignorarías sólo `results/plots` y no `results/data`?

:::::::::::::::  solution

## Solución

Como ocurre con la mayoría de los problemas de programación, hay
varias maneras de resolver esto. Si sólo deseas ignorar el
contenido de `results/plots`, puedes cambiar tu `.gitignore` para
ignorar solamente la subcarpeta `/plots/` añadiendo la siguiente línea a su .gitignore:

`results/plots/`

Si, en cambio, deseas ignorar todo en `/results/`, pero deseas realizar el
seguimiento de `results/data`, puedes agregar `results/` a su .gitignore y
crear una excepción para la carpeta `results/data/`.
El siguiente reto cubrirá este tipo de solución.

A veces el patrón `**` viene muy bien para referirse a múltiples
niveles de directorio. E.g. `**/results/plots/*` hará que git ignore el
directorio `results/plots` en cualquier directorio raíz.



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Incluyendo archivos específicos

¿Cómo ignorarías todos los archivos `.data` en tu directorio raíz, excepto` final.data`?
Sugerencia: Descubre lo que `!` (el signo de exclamación) hace

:::::::::::::::  solution

## Solución

Agrega las siguientes dos líneas a tu archivo .gitignore:

```bash
*.data # ignora todos los archivos .data
!final.data # excepto el archivo final.data
```

El signo de exclamación incluirá una entrada previamente excluida.



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Ignorando todos los archivos de datos en un directorio

Dado un directorio con la siguiente estructura:

```bash
results/data/position/gps/a.data
results/data/position/gps/b.data
results/data/position/gps/c.data
results/data/position/gps/info.txt
results/plots
```

¿Cuál es la regla más corta en `.gitignore` para ignorar todos los archivos `.data`
en `result/data/position/gps`? No ignores el archivo `info.txt`.

:::::::::::::::  solution

## Solución

Agregando `results/data/position/gps/*.data` coincidirá con cada archivo en
`results/data/position/gps` que termine con `.data`.
El archivo `results/data/position/gps/info.txt` no será ignorado.



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## El orden de las reglas

Dado un archivo `.gitignore` con el siguiente contenido:

```bash
*.data
!*.data
```

¿Cuál será el resultado?

:::::::::::::::  solution

## Solución

El modificador `!` anulará algún patrón ignorado previamente definido.
Debido a que la entrada `!*.data` anula todos los archivos` .data` anteriores en `.gitignore`,
ninguno de ellos será ignorado, y todos los archivos` .data` serán rastreados.

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Archivos de bitácora

Supón que escribiste un **script** que crea muchos archivos de registro con la estructura `log_01`, `log_02`, `log_03`, etc. Deseas conservarlos pero no rastrearlos a través de `git`.

1. Escribe **una entrada** en tu archivo `.gitignore` que excluya los archivos con estructura `log_01`, `log_02`, etc.

2. Prueba tu "patrón de ignorar" creando algunos archivos ficticios `log_01`, etc.

3. Te das cuenta de que el archivo `log_01` es muy importante después de todo, así que lo tienes que agregar a los archivos rastreados sin cambiar el` .gitignore` de nuevo

4. Discute con tu compañero de a lado qué otros tipos de archivos podrían residir en tu directorio que no deseas seguir y por tanto excluir a través de `.gitignore`.

:::::::::::::::  solution

## Solución

1. Agrega `log_*` o `log*` como nueva entrada en tu archivo .gitignore
2. Rastrea `log_01` usando `git add -f log_01`
  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::



:::::::::::::::::::::::::::::::::::::::: keypoints

- El archivo `.gitignore` le dice a Git qué archivos ignorar.

::::::::::::::::::::::::::::::::::::::::::::::::::


