---
título: Explorando el History
curso: 25
ejercicios: 0
preguntas:
- "¿Cómo puedo identificar versiones anteriores de archivos?"
- "¿Cómo puedo revisar mis cambios?"
- "¿Cómo puedo recuperar versiones anteriores de archivos?"
objetivos:
- "Explicar qué es el HEAD de un repositorio y cómo usarlo."
- "Identificar y usar  el número de commit the Git."
- "Comparar varias versiones de archivos."
- "Restaurar versiones anteriores de archivos."
puntos clave:
- "`git diff` despliega diferencias entre commits."
- "`git checkout` recupera versiones anteriores de archivos."
---


Como vimos en la lección anterior, podemos referirnos a los commits por sus
identificadores. Puedes referirte a el _commit más reciente_ del directorio de trabajo 
usando el identificador `HEAD`.


Hemos estado agregando una línea a la vez a `mars.txt`, por lo que es fácil rastrear nuestro
progreso, así que hagamos eso usando `HEAD`. Antes de iniciar,
hagamos un cambio a `mars.txt`.

~~~
$ nano mars.txt
$ cat mars.txt
~~~
{: .bash}

~~~
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
An ill-considered change
~~~
{: .output}

Ahora, veamos lo que tenemos.

~~~
$ git diff HEAD mars.txt
~~~
{: .bash}

~~~
diff --git a/mars.txt b/mars.txt
index b36abfd..0848c8d 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1,3 +1,4 @@
 Cold and dry, but everything is my favorite color
 The two moons may be a problem for Wolfman
 But the Mummy will appreciate the lack of humidity
+An ill-considered change.
~~~
{: .output}

lo que es lo mismo que obtendrías si dejas 'HEAD` (intentalo). 
La verdadera bondad en todo esto es cuando puedes referirte a commits previos. Hacemos
esto agregando `~1` para referirnos al commit anterior de `HEAD`.

~~~
$ git diff HEAD~1 mars.txt
~~~
{: .bash}

Si queremos ver las diferencias entre commits anteriores podemos usar `git diff`
nuevamente, pero con la notación `HEAD~1`,`HEAD~2`, y así sucesivamente, para referirse a ellos:

~~~
$ git diff HEAD~2 mars.txt
~~~
{: .bash}

~~~
diff --git a/mars.txt b/mars.txt
index df0654a..b36abfd 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,3 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity
~~~
{: .output}


También podríamos usar `git show`, que nos muestra qué cambios hemos realizado en un commit anterior así como el mensaje del commit, en lugar de las _diferencias_ entre un commit y nuestro directorio de trabajo que vemos usando `git diff`.

~~~
$ git show HEAD~2 mars.txt
~~~
{: .bash}

~~~
commit 34961b159c27df3b475cfe4415d94a6d1fcd064d
Author: Vlad Dracula <vlad@tran.sylvan.ia>
Date:   Thu Aug 22 10:07:21 2013 -0400

    Add concerns about effects of Mars' moons on Wolfman

diff --git a/mars.txt b/mars.txt
index df0654a..315bf3a 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,2 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
~~~
{: .output}


De este modo,
podemos construir una cadena de commits.
El más reciente de la cadena es referido como `HEAD`;
podemos referirnos a commits anteriores utilizando la notación `~`,
así `HEAD~1` (pronunciado "head minus one")
significa "el commit anterior",
mientras que 'HEAD~123` regresa 123 commits desde donde estamos ahora.

También podemos referirnos a los commits usando
esas largas cadenas de dígitos y letras
que `git log` despliega.
Estas son ID únicos para los cambios,
y "unique" realmente significa único:
cada cambio a cualquier conjunto de archivos en cualquier computadora
tiene un identificador único de 40 caracteres.
Nuestro primer commit recibió el ID
`f22b25e3233b4645dabd0d81e651fe074bd8e73b`,
así que probemos esto:

~~~
$ git diff f22b25e3233b4645dabd0d81e651fe074bd8e73b mars.txt
~~~
{: .bash}

~~~
diff --git a/mars.txt b/mars.txt
index df0654a..b36abfd 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,3 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity
~~~
{: .output}


Esa es la respuesta correcta,
pero escribir cadenas aleatorias de 40 caracteres es molesto,
entonces Git nos permite usar solo los primeros caracteres:

~~~
$ git diff f22b25e mars.txt
~~~
{: .bash}

~~~
diff --git a/mars.txt b/mars.txt
index df0654a..b36abfd 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,3 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity
~~~
{: .output}


¡Todo bien! Asi que
podemos guardar cambios en los archivos y ver qué hemos cambiado ahora 
¿cómo podemos restaurar versiones anteriores de las cosas?
Supongamos que accidentalmente sobrescribimos nuestro archivo:

~~~
$ nano mars.txt
$ cat mars.txt
~~~
{: .bash}

~~~
We will need to manufacture our own oxygen
~~~
{: .output}


`git status` ahora nos dice que el archivo ha sido cambiado,
pero esos cambios no se han realizado:

~~~
$ git status
~~~
{: .bash}

~~~
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")
~~~
{: .output}


Podemos volver a poner las cosas tal como estaban
usando `git checkout`:

~~~
$ git checkout HEAD mars.txt
$ cat mars.txt
~~~
{: .bash}

~~~
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
~~~
{: .output}


Como puedes adivinar por su nombre,
`git checkout` recupera (es decir, restaura) una versión anterior de un archivo.
En este caso,
le estamos diciendo a Git que queremos recuperar la versión del archivo grabado en `HEAD`,
que es el último commit guardado.
Si queremos volver más allá,
podemos usar un identificador de commit en su lugar:

~~~
$ git checkout f22b25e mars.txt
~~~
{: .bash}

~~~
$ cat mars.txt
~~~
{: .bash}

~~~
Cold and dry, but everything is my favorite color
~~~
{: .output}

~~~
$ git status
~~~
{: .bash}

~~~
# On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   mars.txt
#
no changes added to commit (use "git add" and/or "git commit -a")
~~~
{: .output}


Ten en cuenta que los cambios están en un área temporal de almacenamiento.
Nuevamente, podemos volver a poner las cosas tal como estaban
usando `git checkout`:

~~~
$ git checkout -f master mars.txt
~~~
{: .bash}

> ## Don't Lose Your HEAD
>
> Above we used
>
> ~~~
> $ git checkout f22b25e mars.txt
> ~~~
> {: .bash}
>
> to revert `mars.txt` to its state after the commit `f22b25e`.
> If you forget `mars.txt` in that command, Git will tell you that "You are in
> 'detached HEAD' state." In this state, you shouldn't make any changes.
> You can fix this by reattaching your head using ``git checkout master``
{: .callout}


Es importante recordar que
debemos usar el número de commit que identifica el estado del repositorio
*antes* del cambio que intentamos deshacer.
Un error común es usar el número de 
commit en el cual hicimos el cambio del que estamos tratando de deshacer.
En el siguiente ejemplo, queremos recuperar el estado antes del más reciente
commit (`HEAD~1`), que es commit `f22b25e`:


![Git Checkout](../fig/git-checkout.svg)


Así que, para poner todo junto,
aqui esta como Git trabaja en forma de dibujos animados:

![http://figshare.com/articles/How_Git_works_a_cartoon/1328266](../fig/git_staging.svg)

> ## Simplificando el caso común
>
> Si lees la salida de `git status` detenidamente,
> verás que incluye esta sugerencia:
>
> ~~~
> (use "git checkout -- <file>..." to discard changes in working directory)
> ~~~
> {: .bash}
>
> Como deciamos,
> `git checkout` sin un identificador de versión restaura los archivos al estado guardado en `HEAD`.
> El doble guión `--` es necesario para separar los nombres de los archivos que se están recuperando
> desde el comando mismo:
> sin esto,
> Git intentaría usar el nombre del archivo como el identificador del commit.
{: .callout}


El hecho de que los archivos pueden revertirse uno por uno
tiende a cambiar la forma en que las personas organizan su trabajo.
Si todo está en un documento grande,
es difícil (pero no imposible) deshacer cambios a la introducción
sin deshacer los cambios posteriores a la conclusión.
Si la introducción y la conclusión se almacenan en archivos separados,
por otra parte,
retroceder y avanzar en el tiempo se vuelve mucho más fácil.

> ## Recuperando versiones anteriores de un archivo
>
> Jennifer ha realizado cambios en el script de Python en el que ha estado trabajando durante semanas, y las
> modificaciones que hizo esta mañana "corrompieron" el script y ya no funciona. Ella ha pasado
> ~ 1hr tratando de solucionarlo, sin tener suerte...
>
> Por suerte, ella ha estado haciendo un seguimiento de las versiones de su proyecto usando Git! ¿Cuáles comandos 
> le permitirán recuperar la última versión estable de su script Python llamado 
> `data_cruncher.py`?
>
> 1. `$ git checkout HEAD`
>
> 2. `$ git checkout HEAD data_cruncher.py`
>
> 3. `$ git checkout HEAD~1 data_cruncher.py`
>
> 4. `$ git checkout <unique ID of last commit> data_cruncher.py`
>
> 5. Ambos 2 y 4
{: .challenge}


> ## Revertir un commit
>
> Jennifer está colaborando en su script de Python con sus colegas y
> se da cuenta de que su último commit en el repositorio del grupo es incorrecto y quiere
> deshacerlo. Jennifer necesita deshacer correctamente para que todos en el repositorio
> del grupo tengan el cambio correcto. `git revert [ID de commit incorrecto]`
> hará un nuevo commit que va a deshacer el commit anterior erroneo de Jennifer. 
> Por lo tanto, `git revert` es diferente de `git checkout [commit
> ID]` porque `checkout` es para cambios locales no comprometidos con el
> repositorio de grupo. A continuación se encuentran los pasos correctos y explicaciones para
> que Jennifer use `git revert`, ¿cuál es el comando que falta?
>
> 1. ________ # Mira el historial de git del proyecto para encontrar la ID del commit
>
> 2. Copia el ID ( los primeros caracteres del ID, e.g. 0b1d055).
>
> 3. `git revert [commit ID]`
>
> 4. Escriba el nuevo mensaje del commit.
>
> 5. Salva y cierra
{: .challenge}

> ## Entendiendo Workflow y History
>
> ¿Cuál es la salida de cat venus.txt al final de este conjunto de comandos?
>
> ~~~
> $ cd planets
> $ nano venus.txt #captura el siguiente texto: Venus is beautiful and full of love
> $ git add venus.txt
> $ nano venus.txt #agrega el siguiente texto: Venus is too hot to be suitable as a base
> $ git commit -m "Comment on Venus as an unsuitable base"
> $ git checkout HEAD venus.txt
> $ cat venus.txt #esto imprimirá el contenido de venus.txt en la pantalla
> ~~~
> {: .bash}
>
> 1.
>
> ~~~
> Venus is too hot to be suitable as a base
> ~~~
> {: .output}
>
> 2.
>
> ~~~
> Venus is beautiful and full of love
> ~~~
> {: .output}
>
> 3.
>
> ~~~
> Venus is beautiful and full of love
> Venus is too hot to be suitable as a base
> ~~~
> {: .output}
>
> 4.
>
> ~~~
> Error because you have changed venus.txt without committing the changes
> ~~~
> {: .output}
>
> > ## Solución
> >
> > Línea por línea
> > ~~~
> > $ cd planets
> > ~~~
> > {: .bash}
> > Entra al directorio 'planets'
> >
> > ~~~
> > $ nano venus.txt #input the following text: Venus is beautiful and full of love
> > ~~~
> > {: .bash}
> > Creamos un nuevo archivo y escribimos una oración, pero el archivo no es rastreado por git.
> >
> > ~~~
> > $ git add venus.txt
> > ~~~
> > {: .bash}
> > Ahora el archivo está en escena. Los cambios que se han realizado en el archivo hasta ahora se confirmarán en el siguiente commit.
> >
> > ~~~
> > $ nano venus.txt #add the following text: Venus is too hot to be suitable as a base
> > ~~~
> > {: .bash}
> > El archivo ha sido modificado. Los nuevos cambios no se realizan porque no hemos agregado el archivo.
> >
> > ~~~
> > $ git commit -m "Comment on Venus as an unsuitable base"
> > ~~~
> > {: .bash}
> > Los cambios que se incluyeron (Venus is beautiful and full of love) se han confirmado. Los cambios que no se realizaron (Venus is too hot to be suitable as a base) no. Nuestra copia de trabajo local es diferente a la copia en nuestro repositorio local.
> >
> > ~~~
> > $ git checkout HEAD venus.txt
> > ~~~
> > {: .bash}
> > Con el checkout, descartamos los cambios en el directorio de trabajo para que nuestra copia local sea exactamente la misma que nuestra HEAD, el más reciente commit.

> >
> > ~~~
> > $ cat venus.txt #this will print the contents of venus.txt to the screen
> > ~~~
> > {: .bash}
> > Si imprimirmos venus.txt obtendremos la respuesta 2.
> >
> {: .solution}
{: .challenge}

> ## Comprobando la compresión de `git diff`
>
> Considera este comando: `git diff HEAD~3 mars.txt`. ¿Qué predices que hará este comando si lo ejecutas? ¿Qué sucede cuando lo ejecutas? ¿Por qué?
>
> Try another command, `git diff [ID] mars.txt`, where [ID] is replaced with
> the unique identifier for your most recent commit. What do you think will happen,
> and what does happen?
{: .challenge}

> ## Getting Rid of Staged Changes
>
> `git checkout` can be used to restore a previous commit when unstaged changes have
> been made, but will it also work for changes that have been staged but not committed?
> Make a change to `mars.txt`, add that change, and use `git checkout` to see if
> you can remove your change.
{: .challenge}

> ## Explore and Summarize Histories
>
> Exploring history is an important part of git, often it is a challenge to find
> the right commit ID, especially if the commit is from several months ago.
>
> Imagine the `planets` project has more than 50 files.
> You would like to find a commit with specific text in `mars.txt` is modified.
> When you type `git log`, a very long list appeared,
> How can you narrow down the search?
>
> Recorded that the `git diff` command allow us to explore one specific file,
> e.g. `git diff mars.txt`. We can apply the similar idea here.
>
> ~~~
> $ git log mars.txt
> ~~~
> {: .bash}
>
> Unfortunately some of these commit messages are very ambiguous e.g. `update files`.
> How can you search through these files?
>
> Both `git diff` and `git log` are very useful and they summarize different part of the history for you.
> Is that possible to combine both? Let's try the following:
>
> ~~~
> $ git log --patch mars.txt
> ~~~
> {: .bash}
>
> You should get a long list of output, and you should be able to see both commit messages and the difference between each commit.
>
> Question: What does the following command do?
>
> ~~~
> $ git log --patch HEAD~3 *.txt
> ~~~
> {: .bash}
{: .challenge}