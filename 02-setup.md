---
title: Configurando Git
teaching: 5
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Configurar `git` la primera vez que utilice la computadora.
- Comprender el significado del flag de configuración `--global`.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- ¿Cómo me preparo para utilizar Git?

::::::::::::::::::::::::::::::::::::::::::::::::::

Cuando usamos Git en una computadora por primera vez,
es necesario configurar algunas cosas. A continuación se presentan algunos ejemplos
de configuraciones que estableceremos a medida que trabajemos con Git:

- nombre y correo electrónico,
-   cuál es nuestro editor de texto preferido,
- y que queremos utilizar estos ajustes globalmente (es decir, para cada proyecto).

En la línea de comandos, los comandos de Git se escriben como `git verb`,
donde` verb` es lo que queremos hacer. Así es como
Drácula configura su nueva computadora:

```bash
$ git config --global user.name "Vlad Dracula"
$ git config --global user.email "vlad@tran.sylvan.ia"
```

Utiliza tu propio nombre y dirección de correo electrónico en lugar de los de Drácula. El nombre de usuario y el correo electrónico se asociarán con tu actividad posterior de Git,
lo que significa que cualquier cambio realizado en
[GitHub](https://github.com/),
[BitBucket](https://bitbucket.org/),
[GitLab](https://gitlab.com/) u
otro servidor de Git
en una lección posterior incluirá esta información.

:::::::::::::::::::::::::::::::::::::::::  callout

## Finales de línea

Al igual que con otras teclas, cuando haces click en la tecla 'Enter' de tu teclado,
tu computadora codifica este input como un caracter.
Por razones que son demasiado largas para explicar aquí, diferentes sistemas operativos
usan diferentes caracteres para representar el final de una línea.
(También son conocidas como *newlines* o *line breaks*.)
Como Git usa éstos caracteres para comparar archivos,
esto puede causar problemas inesperados cuando se edita un archivo en máquinas diferentes.

Puedes cambiar el modo en que Git reconoce y codifica finales de línea
usando el comando `core.autocrlf` con `git config`.
Se recomiendan las siguientes configuraciones:

En OS X y Linux:

```bash
$ git config --global core.autocrlf input
```

Y en Windows:

```bash
$ git config --global core.autocrlf true
```

Puedes leer más sobre este tema
[en esta página de GitHub](https://help.github.com/articles/dealing-with-line-endings/).


::::::::::::::::::::::::::::::::::::::::::::::::::

Para estas lecciones, estaremos interactuando con [GitHub](https://github.com/), por lo tanto la dirección de correo electrónico utilizada debe ser la misma que utilizaste al configurar tu cuenta de GitHub. Si te preocupa la privacidad, revisa [las instrucciones de GitHub para mantener tu dirección de correo electrónico privada][git-privacy].
Si eliges utilizar una dirección de correo electrónico privada con GitHub, usa la misma dirección de correo electrónico para el valor `user.email`, por ejemplo, `username@users.noreply.github.com`  reemplazando` username` con tu nombre de usuario de GitHub. Puedes cambiar la dirección de correo electrónico posteriormente utilizando el comando `git config` nuevamente.

Drácula también tiene que establecer su editor de texto favorito, siguiendo esta tabla:

| Editor                     | Comando de configuración | 
| :------------------------- | :----------------------- |
| Atom                       | `$ git config --global core.editor "atom --wait"`                         | 
| nano                       | `$ git config --global core.editor "nano -w"`                         | 
| TextWrangler (Mac)         | `$ git config --global core.editor "edit -w"`                         | 
| Sublime Text (Mac)         | `$ git config --global core.editor "subl -n -w"`                         | 
| Sublime Text (Win, 32-bit) | `$ git config --global core.editor "'c:/program files (x86)/sublime text 3/sublime_text.exe' -w"`                         | 
| Sublime Text (Win, 64-bit) | `$ git config --global core.editor "'c:/program files/sublime text 3/sublime_text.exe' -w"`                         | 
| Notepad++ (Win, 32-bitl)   | `$ git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`                         | 
| Notepad++ (Win, 64-bit)    | `$ git config --global core.editor "'c:/program files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`                         | 
| Kate (Linux)               | `$ git config --global core.editor "kate"`                         | 
| Gedit (Linux)              | `$ git config --global core.editor "gedit --wait --new-window"`                         | 
| Scratch (Linux)            | `$ git config --global core.editor "scratch-text-editor"`                         | 
| emacs                      | `$ git config --global core.editor "emacs"`                         | 
| vim                        | `$ git config --global core.editor "vim"`                         | 
| Visual Studio Code         | `$ git config --global core.editor "code --wait"`                         | 

Es posible reconfigurar el editor de texto para Git siempre que quieras.

:::::::::::::::::::::::::::::::::::::::::  callout

## Saliendo de Vim

Ten en cuenta que `vim` es el editor por defecto para muchos programas, si no has utilizado` vim` antes y deseas salir de una sesión, presiona la tecla `Esc` y posteriormente escribe `: q!` y `Enter`.


::::::::::::::::::::::::::::::::::::::::::::::::::

Los cuatro comandos que acabamos de ejecutar sólo se tienen que ejecutar una vez: la flag `--global` le dice a Git que use la configuración para cada proyecto, en tu cuenta de usuario, en esta computadora.

Puedes comprobar tu configuración en cualquier momento:

```bash
$ git config --list
```

Puedes cambiar la configuración tantas veces como quieras: sólo usa los mismos comandos para elegir otro editor o actualizar tu correo electrónico.

:::::::::::::::::::::::::::::::::::::::::  callout

## Proxy

En algunas redes es necesario usar un
[proxy](https://en.wikipedia.org/wiki/Proxy_server). Si este es el caso, es
posible que también necesites proporcionarle a Git el proxy:

```bash
$ git config --global http.proxy proxy-url
$ git config --global https.proxy proxy-url
```

Para deshabilitar el proxy, utiliza

```bash
$ git config --global --unset http.proxy
$ git config --global --unset https.proxy
```

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout

## Ayuda y manual de Git

Ten presente que si no recuerdas algún comando de  `git`, puedes acceder a la lista de comandos utilizando la opción `-h` y al manual de Git con la flag `--help` :

```bash
$ git config -h
$ git config --help
```

::::::::::::::::::::::::::::::::::::::::::::::::::



[git-privacy]: https://help.github.com/articles/keeping-your-email-address-private/


:::::::::::::::::::::::::::::::::::::::: keypoints

- Use `git config` para configurar un nombre de usuario, email, editor, y otras preferencias.

::::::::::::::::::::::::::::::::::::::::::::::::::


