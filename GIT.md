# GIT

Sistema de Control de Verisón Distribuido.

## Distribuido
Lo que hay Distribuido son repositorios.
Al trabajar con git en un proyevto tenemos muchos repositorios.
Todos son distintos entre si.

## Zonas de tranajo
- Working dir: Carpeta de trabajo... en mi ordenador
	- Es donde trabajo.... donde hago cambios
- Area de staging: Preparación
	- Preparamos cambios para subirlos a nuestro repo local
- Repositorio local
	- Guarda commits (fotos cerradas y selladas de mi proyecto)
- Repositorios remotos:
	- sincronizar repos locales entre participantes de un proyect

## Area de preparacion y el repo local, se encuentran ambos dentro de la carpeta .git

# Commit:

Foto (snapshot) de un momento dado de nuestro proyecto... pero incluyendo solamente los cambios que yo deseo.
Un commit siempre está ligado al menos en 1 rama...opcionalmente más.

## Cambios:
Crear un archivo
Mover un archivo
Eliminar un archivo 
Cambiar un archivo

Git no controla ningún cambio.

## Cuadno hacer un commit:
Queremos commits frecuentes, puntuales (una única funcionalidad) y en caso de meter varias funcionalidades, que no se mezclen tipos de funcionalidad

# Configuracion de GIT:
se hace mediante propiedades (clave, valor)
Las propiedades van en grupos 

- git config --global: Este parámetro aplica una configuración a nivel global de la máquina

para trabajar con ellas utilizamos el git config

# HEAD
Es una variable, que apunta a un determinado commit.
Por defecto apunta al último commit de la rama en la que estoy.
Para cambiar el commit al que apunta el HEAD:
	$ git chekout
El commit al que apunta el HEAD es el que visualizo en el working dir (en mi carpeta)

# Trabajando en local con git
### Comandos
$ git init: Crea un repo local
### Cómo está mi proyecto?
$ git status
### Comenzar a controlar archivos en el proyecto
$ git add RUTA
$ git add *
	Todos los archivos NO OCULTOS de la carpeta en la que estoy y sus subcarpetas
$ git add .
	Todos los archivos OCULTOS Y NO OCULTOS de la carpeta en la que estoy y sus subcarpetas
$ git add :/
	Todos los archivos OCULTOS Y NO OCULTOS desde la carpeta raiz... da igual donde esté yo en la terminal

IMPORTANTE: esto hace una copia del fichero en el área de preparación.
Llegados a este punto tenemos 2 copias del archivo.

### Eliminar un fichero del área de staging y de control por git
$ git rm --cached FICHERO

Si no pongo el --cached:
$ git rm FICHERO 
	El fichero se borra de totdos los sitios: Carpeta de trabajo... y del área de staging

### Recuperar un fichero ya eliminado previamente pero solo si ya lo tengo commiteado
$ git restore FICHERO

### Consultar el historial
$ git log
$ git log --oneline

### Ver diferencias entre archivos(y sus versiones)
$ git diff FICHERO
	Las diferencias entre la carpte de trabajo y el área de staging
$ git diff HEAD FICHERO
	Las  entre la carpeta de trabajo y el commit
$ git diff --cached FICHERO
	Las diferencias entre el area de staging y el ultimo commit

### Comitear cambios
$ git commit -m "mensaje de confirmacion"
$ git ocmmit -am " segundo commit"
	Añade automaticamente cambios al área de staging
	Solo cambios sobre ficheros ya controlados por git

$ Variable HEAD
	HEAD       		 	Ultimo commit
	HEAD^ HEAD~   	 	Penultimo commit
	HEAD ^^ HEAD~2   	Antepenultimo commit
	HEAD ^^^ HEAD~3  

### Control de archivos en mi carpeta/proyecto
$ git rm RUTA:
	Elimina permanentemente el fichero de mi carpeta y del área de staging...
	Y le indica a git que deje de controlar ese archivo
$ git rm --cached RUTA
	Elimina del área de staging...
	Y le indica a git que deje de controlar ese archivo
$ git mv ORIGEN DESTINO
	Comando mover
	Mueve el archivo en todos sitios...
	Se puede perder el historial de cambios sobre el archivo

$ git cherry-pick 

# Reescribir el historial del proyecto (local)

### Modificar el último commit me reescribe el ultimo commit
$ git commit --amend
Esto solo si el commit no ha salido de mi máquina (de mi repo local)
Esto aplica a todos lo comandos de reescritura del historial

# Los archivos en GIT tiene 4 estado
U Untracked:	 Sin seguimiento 
M Modified: 	 hay seguimiento y está cambiado
D Deleted: 		 
A Added

### Operaciones matematicas

# Git checkout:
- Restaurar archivos, deshaciendo cambios
	git restore
- Cambiar a una rama
	git switch
- Cambiar el HEAD

$ git reset --hard: me deshace todo lo que hecho desde el ultimo commit de todo lo que tengo en el proyecto

Cuando creamos un commit, los commits llevan un orden secuencial... uno detrás de otro (al menos a nivel de rama).

git checkout - es el equivalente al cd - en linux me lleva al anterior en donde estuviera

Reescribir el historial:
git commit --amend: Modifica el utlimo commit

git reset --TIPO: Trabaja en 3 sitios
--hard
	- Working dir
	- Area de preparación (staging)
	- Repo
--mixed
	- Area de preparación (staging)
	- Repo
--soft
	- Repo

git reset --soft HEAD~3
- Vuelvo 3 commit atras
- Borra los commits siguientes en el repo
- No se borra nada en mi carpeta 

git rebase -i:
	Reescribir el historial

git rebase: Fusiana ramas