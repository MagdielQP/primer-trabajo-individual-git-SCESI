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

## Ver modificaciones en git
 - con el siguiente comando podemos ver los eleementos modificados(en area de staging) en nuestro proyecto despues de un commit, pero esta no es la mejor forma(es mejor una herramienta grafica en el editor de codigo):
    - $ git diff --cached
 - Si queremos ver los cambios hechos en el area de ,modified entonces solo colocamos el comando:
    - $ git diff
 - Para limpiar nuestra area de trabajo y descartar cambios podemos usar:
    - $ git clean -f OJO: usar esto es peligroso, tratar de no usarlo 

## Head y main
 - main: este llegaria a ser el nombre principal de la rama principal, o seria donde nos ubicamos nosotros(cambia dependiendo de la rama donde nos encontremos)
 - head: indica donde nos encontramos nosotros en el codigo, y este siempre va a apuntar a una rama en especifico.

# Ignorando archivos y directorios - agregar un archivo al gitignore despues de creado este
 - Que archivos ignorar?
      • Archivos que tengan credenciales o llaves de API (no deberías subirlas al
      repositorio, simplemente inyectarlas por variable de entorno)
      • Carpetas de configuración de tu editor (/.vscode)
      • Archivos de registro (log files)
      • Archivos de sistema como .DS_Store
      • Carpetas generadas con archivos estáticos o compilaciones como /dist o /build
      • Dependencias que pueden ser descargadas (/node_modules)
      • Coverage del testing (/coverage)
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

## Como deshacer el ultmo commit
Con el comando reset hacemos que la rama actual retroceda a la revisión que le indicamos
 - Si se quiere mantener los ultimos cambios:
    - $ git reset --soft HEAD~1  //HEAD~1 hace que obtengamos el ultimo commit
El parámetro --soft es el que va a hacer que los cambios que habíamos hecho en el commit, en lugar de eliminarlos, nos los mantenga como cambios locales en nuestro repositorio
al ejecutar este comando, no se eliminarán los cambios del commit, sino que se mantendrán como cambios locales
 - Si no se quiere mantener los cambios:
   - $ git reset --hard HEAD~1

## Arreglar el comentario en el commit
 - Si sólo quieres arreglar el mensaje que has usado para el último commit:
   - $ git commit --amend -m "Este es el mensaje correcto"
 - Si se quiere añadir más cambios al último commit:
   - $ git commit --amend -m "Mensaje del commit"

## git checkout
Este comadno nos ayudara a "volver en el pasado" por asi decirlo, lo q hace es q podamos ir a versiones anteriores, lo q si debemos tener en cuenta es q si realizamos comits una vez idos a versiones anteriores, estos no se guardaran (para ello mejor podriamos crear ramas)
   - $ git checkout id_de_commit
 - una vez usado el comando, si usamos git log, solo nos mostrara las versiones anteriores a esta, y no todas, para ver todas usaremos el comando:
   - git log --oneline --all
 - Para volver al commit de la cabecera usaremos el comando:
   - git checkout main
otra funcionalidad de este comando es recuperar archivos eliminados especificos
primero revisamos donde se uso por ultima vez el archivo con:
    - $ git log --oneline -- archivo_eliminado
nos mostrara el log de los commits donde estaba el archivo antes de eliminar, entonces escogemos cualquiera que queramos y copiamos su id:
    - git checkout id_commit archivo_eliminado

## ver los aportes de un usuario
El siguiente comando nos mostrara todos los mensajes y el nro de commits de nuestro usuario.
   - git shortlog
   - git shortlog -s "muestra el nombre de usuario y el numero de commits"

# RAMAS, Que son?
Podria decirse que es una copia del proyecto, donde podremos realizar todos los cambios que queramos sin afectar al main, podriamos incluirlo despues de verificar que los cambios estan bien.
Una rama es una versión del repositorio que se crea a partir de un commit

## Creando ramas
 - Para crear una nueva rama(no se puede crear ramas con el mismo nombre)
   - $ git branch mi-primera-rama
 - Para cambiar a una rama:
   - $ git switch mi-primera-rama
 - Para realizar los dos pasos anteriores (crear nueva rama y cambiarse a esta)
   - $ git switch -c mi-primera-rama
 - Antes del comando switch se usaba checkout, pero ahora no:
   - $ git checkout -b mi-primera-rama
 - Listar las ramas 
   - $ git branch
 - Cambiar de nombre a una rama
   - $ git branch -m nombre_antiguo nombre_nuevo
 - Comparar todos los commits en una rama con el main: (en vez de main puede ser el nombre de otra rama)
   - $ git log main..nombre_otra_rama
 - Para ver todos loa cambios en una rama comparados con el main:
   - $ git diff main..nombre_otra_rama
## Stash
Podria decirse que el stash es un area de guardado el cual se usa cuando queremos cambiar de ramas y no hemos echo un commit(cuando no hay suficiente avance para realizar un commit y no lo hemos realizado), ya que git no te deja cambiar de ramas si se hicieron modificaciones en el archivo.
Para solucionar ese problema esta el area de stash, agregamos nuestros cambios asi:
   - $ git stash push -m "Cambios a..."
 - Para listar todos losarchivos que estan en el stash:
   - $ git stash list
 - Para ver el contenido de un stash
   - $ git stash show 1 (1 es el nombre del indice del stash, podemos verlo al hacer stash list)
 - Para traernos algun cambio en especifico del stash para hacer commit despues usamos:
   - $ git stash apply 1 (1 es el numero en el stash que se quiera traer, cambiarlo por el q quieras)
cuando usamos apply no se borran los los stash del area de stash para ello debemos eliminar el stash que sacamos con apply o limpiar toda el area de stash.
 - Para borrar solo un stash especifico con su nro de id:
   - $ git stash drop 1
 - Para limpiar toda el area del stash usamos:
   - $ git stash clear
para no estar usando apply y luego eliminarlo usamos:
 - Para sacar del stash y eliminarlo usamos:
   - $ git stash pop
## Fusionar ramas
### Fast-forward
Cuando ene cierto punto de nuestro main sacamos una rama, hacemos cambios en esta y no en el main(mantenemos el main como cuando sacamos la rama que fuimos modificando), esto hace que podamos hacer commit con el main sin necesidad de crear otro commit por parte del main, es una forma mas directa.
en pocas paabras: Cuando no se a modificado el main y se hace merge de otra rama al main

### Three way merge
Cuando sacamos una rama del main y luego modificamos la rama, y tambien se modifica el main, esto hace que se cree un nuevo commit que incluya los cambios del main, de la rama y tambien del commit desde donde se dividio la rama.
En pocas palabras: mezcla los cambios de la rama, del main y las compara con las que hay en el commit de donde se dividio la rama.

### Como hacerlo
 - Primero verificamos que estamos en la rama destino:
   - $ git branch --show-current
 - ahora vamos a incorporar a nuestro destino los cambios de la rama:
   - $ git merge my-branch
 - Si no queremos usar Fast-forward, entonces:
   - $ git merge --no-ff nombre_rama  (esto hace que se cree una rama intermerida como lo visto en 3 way merge y hace q se nos abra el editor que colocamos por defecto para poder editar el mensaje del commit, cosa que en fast-forward no pasa)
Punto importante:
cuano realizamos cambios en la rama main y en la rama-creada, y no usamos --no-ff y lo hacemos de manera directa con merge, esta automaticamente detecta que es 3-way-merge y nos lleva al editor de codigo para editar el nombre o dejar el que nos da por defecto.
 - Para eliminar una rama hacemos:
   - $ git branch -D nombre_archivo

## Conflictos al hacer merge
Esto sucede cuando se toca la misma linea de codigo en las ramas que se estan fusionando
 - para evitar el commit o abortar el commit se hace:
   - git merge --abort
Para resolver conflictos podemos usar el diff o el editor de nuestro gusto(en este caso visual Studio) para poder ver mejor los cambios o conflictos en el codigo
Una vez solucionado el conflicto podremos hacer commit sin problemas

## Revertir cambios despues de un merge entre dos ramas
 - usamos el comando y se crea un nuevo cambio con los cambios revertidos seleccionados:
   - $ git revert -m 1 HEAD     (el numero despues de -m indica a que "padre" o estado vamos  volver, ya que merge une dos ramas, debemos elegir a cual vamos a volver, 1 podria ser main y 2 la otra rama)

## Agregar archivos de otras ramas
 - Cuando necesitemos traer un archivo desde otra rama a la nuestra entonces usamos:
   - $ git restore --source=rama_otra -- nombre_archivo

## traer cambios de un commit anterior de otra rama
 - cuando una rama no ha sido fusionada y se quiere traer cambios de un commit anterior de esta, hacemos:
   - $ git cherry-pick id_commit_rama

## rebase
Es un comando que permite integrar modificaciones de una rama a otra, reorganizando o cambiando la base de una rama de commit a otra, lo que hace que parezca que la rama se ha creado desde un commit diferente
OJO: Solo hacerlo cuando solo una persona esta desarrollando en esta rama.
ahora nos debemos asegurar que estamos en la rama a la cual le queremos cambiar la base o la cual queremos estar juntando con el main(mayormente se junta con el main)
se usa el comando:
   - $ git rebase main
 - Si hay conflictos hay mas opciones como:
   - $ git rebase --continue (continuar despues de resolver conflictos)
   - $ git rebase --skip (se utiliza para continuar una operación de rebase omitiendo el commit que causó un conflicto)
   - $ git rebase --abort (abortar el rebase)