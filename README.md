# APUNTES Y EXTRAS DE GIT

## En este archivo se guardara todos los apuntes de clases e informacion que extraeremos del libro u otras fuentes, el archivo .py mostrara un resumen mas general de lo avanzado en clase

## ¿Que es git?
 - Es un sistema de control de versiones(permite almacenar codigo)
 - Provee funcionalidades como buscar codigo, saber en que hora se introdujo este y que persona lo hizo
 - tambien no permite volver a versiones anteriores (ejempl: si hay errores en un repositrio actual, podemos ir a unas versiones antes donde este error no estaba)

## Instalacion
 - Para instalar lo que seria gt, este se puede instalar tanto en sistemas MacOS, Linux, Windows desde la pagina oficial:[pagina-git](https://git-scm.com/)
 - Una vez instalado hay alguna casillas por marcar, lo cual se recomienda seguir las intrucciones echas por el instructor.

 ## Inicios
 - Una vez instalado podemos ir a configurar el nombre y el correo que git usara para ello podemos configurarlo desde la terminal de git con los comandos:
    - $ git config --global user.name "<tu nombre>"
    - $ git config --global user.email "<tu email>"
 - Si por algun motivo quisieras editarlo desde tu editor de codigo entonces lo haremos con el comando:
    - $ git config --global -e
 - lo que hace este comando es q nos abre una pestaña en el editor que usamos y nos muuestra la informacion de [user, init, core, filter"lfs"]
 ![imagen de muestra]("Imagen de WhatsApp 2025-04-30 a las 08.01.24_edf6970f.jpg")
 - tambien podemos confirmar la configuracion con los comandos:
    - $ git config --list
    - $ git config --global --list
 - tambien tenemos el comando para ver de donde proviene cada configuracion:
    - $ git config --list --show-scope
## Programas visuales
 - Estos programas ayudaran a poder administrar mejor nuestros repositorios en el IDE o editor de preferencia, extensiones como: GitLens o Sourcetree.