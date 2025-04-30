# APUNTES Y EXTRAS DE GIT

## En este archivo se guardara todos los apuntes de clases e informacion que extraeremos del libro u otras fuentes, el archivo .py mostrara un resumen mas general de lo avanzado en clase

# INICIOS EN GIT
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

# PRIMEROS PASOS - CREACION DE UN RESPOSITORIO
En esta parte estaremos creando un repositorio y tambien estaremos entendiendo algunos conceptos importantes que nos ayudaran a entender los estados antes de guardar la informacion en el repositorio.

## Estados
 - Tenemos 3 estados:
    - Modified: El archivo contiene cambios que no han sido confirmados.
    - Staged: El archivo ha sido marcado como listo para ser confirmado.
    - Commited: El archivo se encuentra grabado en el repositorio local.
## Creando un nuevo repoitorio
Antes de crear un nuevo repositorio asegurate de estar en la carpeta donde deseas crear el repositorio.
Una vez nos aseguramos de haberlo creado, nos dirijimos a la carpeta a donde colocaremos el repositorio y creamos el repositorio con los comando:
    - $ git init
 - Tambiien podriamos crear directamente la carpeta con el repositorio con:
    - $ git init nombre-proyecto
una vez creado el repositorio podemos ver los archivos que nos creo con el comando:
    - $ ls -a
 - Este mostara varios archivos que no es importante por el momento el saber que hcaen, pero:
 > [!WARNING]
 > No borrar el archivo .git sino tendremos terribles problemas...

  - Otra manera de ver que hemos iniciado un repositorio es:
    - $ git status
Este comanado nos muestrara el estado actual de nuestro repositorio, si este no existiera nos mandara un mensaje como:
    fatal: not a git repository (or any of the parent directories): .git
Pero si este si tuviera un repositorio inicializado nos mostraría:
    git status
    On branch main
    No commits yet
    nothing to commit (create/copy files and use "git add" to track)
## agregando al Stage
 - El area de staging nos sirve para crear "propuestas" en donde si hay un error es mas facil volver los archivos al area de modificacion(estado anterior) 
- Para agregar al Stage que como vimos es el estado intermedio entre la modificacion y el commit, usamos el comando:
    - $ git add nombre-de-archivo-a-añadir
 - si no queremos colocar archivo por archivo al repositorio entonces usamos el comando:
    - $ git add . 
    - $ git add -A
    - $ git add --all 
Este comando coloca en el Stage todos los archivos que han sido modificados.

## Deshacer un archivo modificado (que este en el stage)
- Cuando un archivo fue pasado al estado de Stage todavia podemos volver este a su estado anterior antes de estar agregado a esta area, para ello usamos los comandos:
    - $ git reset nombre-archivo
Tambien podemos usar el comando:
    - $ git restore --staged nombre_archivo

## Deshacer un archivo ya modificado
 - Para restaurarlo a la version previa usamos el comando:
    - $ git restore nombre-archivo
 - o para seleccionar varios archivos podemos usar:
    - git restore .
    - git restore '*.py'

# Que es un commit
un commit resgistra los cambios dentro del repositorio local, estos guardan el id, la fecha y hora, autor, y la referencia a la instantanea
En español significa "comprometer".
un commit toma todo lo que esta en el area de staging y lo guarda en el repositorio local.
cuando se hace commit OJO: no se elimina la parte del staging

## Haciendo un commit
Para hacer commit verificamos que todo lo que queremos commitear este en el area de staging.
Si tenemos dudas al realizas commit podemos usar:
    - $ git commit -h
    ESto nos ayudara a ver que comando mas podriamos usar despues del commit.

para hacer commit podemos usar los comandos:
    - $ git commit
    esto nos abrira una pestaña en nuestro editor de codigo conde podremos añadir un titulo y un mensaje de referencia al commit que estamos haciendo.
    - $ git commit -m "titulo para el commit"
    con este comando colocamos el titulo para q ya no abra una pestaña en nuestro editor de codigo.
    - $ git commit -m "titulo de referencia"-m "descripcion o mensaje mas largo"
 - Para realizar commits y saltarse la parte del staging (usar add) usaremos:
    - $ git commit -a -m "titulo de commit"
    o de manera mas simplificada:
    - $ git commit -am "titulo de commit"

## Buenas practicas en los commits
 - Cuando hacemos commits debemos verificar que al hacerlos no deberian ser cambios muy grandes que contengan una gran cantidad de modificaciones, ni tampoco que sean muy pequeños como una linea de codigo, para hacer un commit ponte a pensar...
    - "En un futuro si algo sale mal podria volver a este punto"
 - Los mensajes o titulos de los commits deben de hacer sentido, osea, deben ser bien descriptivos.

 ## Ver el historial de commits
  - Para ver el historial de commits con sus respectivos detalles usamos los comandos:
    - $ git log
    Esto mostrara en detalle el id,autor, fecha y hora
    - $ git log --oneline
    como lo dice el nombre, este comando nos simplifica dandonos solo el titulo y el id.
 - para ver el historial pero de forma que sea desde el mas antiguo al mas nuevo usamos el comando:
    - $ git log --oneline --reverse
 - Tambien tenemos la opcion de ver el historial en forma de grafo con el comando:
    - $ git log --online --graph
 - Si los commit son muchos, podemos usar un comando:
    - $ git log --online -5 //ejm -5 muestra los ultimos 5 commit.
 - Si queremos ver en el historial despues o antes de una fecha usamos:
    - $ git log --online --after="2025-03-1"
    - $ git log --online --after="one month ago"
    - $ git log --online --before="last week"
    - $ git log --online --after="last week" --before="yesterday" //commits entre ayer y hace un mes atras
 - Buscar codigo modififcado dentro de un commit:
    - $ git log --online -S"codigo_a_buscar"
    - $ git log --online -S"codigo_a_buscar" --patch //mostrara lineas que se agregaron y quitaron con el pedazo de codigo
    - $ git log --online -S"codigo_a_buscar" --stat //musetra solo los archivos que cambiaron
## Algunas cositas extras
 - git no detecta automaticamente cuando se cambia un nombre o se mueve un archivo a otra carpeta, asi que podemos usar el siguiente comando:
    - $ git mv archivo.py nombre-carpeta
 - para ver una version mas resumida o simplificada de status podemos usar el comando:
    - $ git status -s
- A veces entrar al historial te pide presionar "q" para salir del historial.
- con el siguiente comando podemos ver detalles sobre el commit:
    - $ git show id-commit
- con el siguiente comadno podemos ver el contenido de un commit o de un archivo que esta en el commit:
    - $ git show id-commit:nombre_archivo
 - con el siguiente comando podemos ver los eleementos modificados(en area de staging) en nuestro proyecto despues de un commit, pero esta no es la mejor forma(es mejor una herramienta grafica en el editor de codigo):
    - $ git diff --cached
 - Si queremos ver los cambios hechos en el area de ,modified entonces solo colocamos el comando:
    - $ git diff
 - Para limpiar nuestra area de trabajo y descartar cambios podemos usar:
    - $ git clean -f OJO: usar esto es peligroso, tratar de no usarlo 

## Head y main
 - main: este llegaria a ser el nombre principal de la rama principal, o seria donde nos ubicamos nosotros(cambia dependiendo de la rama donde nos encontremos)
 - head: indica donde nos encontramos nosotros en el codigo, y este siempre va a apuntar a una rama en especifico.

# Ignorando archivos y directorios
 - crear un archivo ".gitignore"
 en este archivo agregamos todos los arvchivos que queremos ignorar
 - Una vez un archivo agregado y ya tiene seguimiento de git es muy dificil ignorarlo, es decir, si un archivoi ya a tenido seguimiento, y despues lo agregamos a un .gitignore, y editamos ese archivo, este va a salir que esta modificado, cuando al estar en el gitignofe no deberia ser asi, arreglamos esto haciendo:
    - $ git rm --cached archivo_a_ignorar 
 ## Restaurar un archivo a una version anterior
 - usamos el comando:
    - $ git restore --source=id_commit archivo_a_recuperar     o tambien podemos usar:
    - $ git restore --source=HEAD~1 archivo_a_recuperar     //HEAD~1 vuelve a un commit atras
## crear shortcuts o alias
 - para ello usamos los comandos:
    - $ git config --global alias.nombre_alias "comando que quieres acortar"
    ejm: $ git config --global alias.glg "log --oneline --graph"