1. [Comandos básicos](#comandos-basicos)
    1.1. [Antes de empezar](#antes-de-empezar)
    1.2. [Configurar Git](#configurar-Git)
    1.3. [Clonar un repositorio](#clonar-un-repositorio)
    1.4. [Añadir un fichero](#añadir-un-fichero)
2. [Empezar con un proyecto desde cero](#empezar-con-un-proyecto-desde-cero)
    2.1. [Crear un proyecto desde cero](#crear-un-proyecto-desde-cero)
    2.2. [Listado mostrando carpetas ocultas](#listado-mostrando-carpetas-ocultas)
    2.3. [Git commit](#git-commit)
    2.4. [Eliminar proyecto](#eliminar-proyecto)
3. [Añadir Git a un proyecto existente](#añadir-git-a-un-proyecto-existente)
    3.1. [Situarte en el directorio que quieras desde la raiz](#situarte-en-el-directorio-que-quieras-desde-la-raiz)
    3.2. [Inicializar Git](#inicializar-Git)
    3.3. [Añadir fichero](#añadir-fichero)
    3.4. [Commit fichero](#commit-fichero)
    3.5. [Eliminar repositorio](#eliminar-repositorio)
4. [Trackear Archivos en Git](#trackear-archivos-en-git)
    4.1. [Añadir cambios + mensaje para commit en la misma orden](#añadir-cambios-+-mensaje-para-commit-en-la-misma-orden)
    4.2. [Ver listado de archivos trackeados](#ver-listado-de-archivos-trackeados)
    4.3. [Añadir ficheros paso a paso](#añadir-ficheros-paso-a-paso)
    4.4. [Uso de add](#uso-de-add)
    4.5. [Añadir ficheros y carpetas recursivamente](#añadir-ficheros-y-carpetas-recursivamente)
    4.6. [Descartar Cambios](#descartar-cambios)
    4.7. [Renombrar Ficheros](#renombrar-ficheros)
    4.8. [Borrar Ficheros](#borrar-ficheros)
    4.9. [History](#history)
    4.10. [Alias](#alias)
    4.11. [Ignorar Ficheros](#ignorar-ficheros)
8. [Trabajar con Ramas](#trabajar-con-ramas)
    6.1. [Listar ramas](#listar-ramas)
    6.2. [Crear una nueva rama](#crear-nueva-rama)
    6.3. [Renombrar ramas](#renombrar-ramas)
    6.4. [Borrar ramas](#borrar-ramas)
    6.5. [Crear y moverse a una rama en un solo paso](#crear-y-moverse-a-una-rama-en-un-solo-paso)


# Comandos básicos

## Antes de empezar
Si quieres conocer el directorio en el que te encuentras, escribe:
```
pwd
```
## Configurar Git

Para operar con git tenemos que dejar el mismo nombre y dirección de correo en git en el terminal. **2 órdenes**
```
git config --global user.name “Nombre de usuario”
git config --global user.email “nombre@email.com”
```

Para ver que esas dos órdenes han tenido efecto y todos los parametros que puedes configurar
```
git config --global --list
```

Para limpiar la pantalla y tener una terminal limpia
```
clear
```

Para obtener ayuda de Git y la segunda para obtener ayuda sobre un tema en concreto.
```
git help
git help commit
``` 

## Clonar un repositorio

```
git clone URL DEL REPOSITORIO
```

## Añadir un fichero

```
echo "Texto que aparecerá al inicio del fichero" >> NombreFiechero.md
```
Para ver el contenido del fichero
```
cat NombreFiechero.md
```
Si hacemos un git status nos dirá que hay **Untraked files**. Esto quiere decir que este fichero está en nuestro **working directory** pero aún no está añadido a Git para ser trackeado. Para añadir este nuevo fichero a git usar la orden **add**
```
git add NombreFiechero.md
```
Ahora este fichero está en el Staging Area. Este area está diseñada para que podamos hacer añadidos o modificaciones incrementales y finalmente añadir mediante un commit todos los cambios realizados a nuestro **Local Ropository** (aún en nuestro ordenador) y finalmente subirlo al **Remote Repository**, en nuestro caso GitHub.
```
git commit -m "mensaje del commit con el resumen de lo que hayamos hecho"
```
Ahora si hacemos un git status la terminal nos informará de que nuestro **working directory** está limpio y que (en nuestro caso) master branch está por delante del master en por un commit. Es decir, podemos ir añadiendo commits en nuestro Local Repository para luego añadirlos al **Remote Repository**.

Para subir nuestro fichero y nuestros cambios al **Remote Repository** solo tenemos que hacer
```
git push origin master
```
En este caso **origin** es nuestro repositorio en GitHub (podemos acceder a esta información en la parte de config) y **master** se refiere a nuestra, de momento, única rama en el repositorio.


# Empezar con un proyecto desde cero

## Crear un proyecto desde cero

Para crear desde cero un proyecto con un repositorio de GIT. Para hacer esto necesitamos utilizar el comando **init**
```
git init nombre-del-proyecto
```
## Listado mostrando carpetas ocultas

Con esto habremos creado una carpeta vacia (sin ficheros visibles) que será el repositorio local que git controlará. Al hacer un **ls** en el terminal veremos que se ha creado una carpeta. Al entrar en ella con el comando **cd** y ejecutar de nuevo el comando **ls** vemos que no existe ningún fichero visible. Ahora si queremos ver los ficheros ocultos:
```
ls -al
```
## Crear fichero desde la terminal

Ahora podemos ver que existe una carpeta oculta **.git** si accedemos a ella a través de **cd** y listamos su contenido podemos ver la estructura del repostorio de git. Al vover a la carpeta donde se encuentra el **working repository** con **cd ..** podemos crear un fichero desde cero.

```
touch nombre-fichero.md
open nombre-fichero.md
```

Con **touch** creamos un fichero y con **open** lo abrimos con las herramienta que tengamos configurada por defecto para trabajar con ese tipo de fichero.

Si preguntamos con **git status** se nos informará de que existe un nuevo fichero en el **working directory** que aún no está siendo trackeado **staging area** por git. Lo tendremos que añadir mediante **add**

## Git commit

```
git commit
```

Podemos hacer un commit de varias líneas, pero vas a realizarlo por defecto dentro de la terminal, para salir de esta vision. Presiona primero **escape** y luego:

```
:wq
```
**:** entra en el modo de comando, **w** es para "escribir" (guardar) y, **q** es para salir.  
Con esto hemos pasado el fichero al repositorio Git y habrá un historial de commits que posteriormente podremos recuperar.

## Eliminar proyecto

Ahora simplemente vamos a eliminar todo el proyecto y el repositorio de git, para ello nos tenemos que situar en la carpeta origen del proyecto y ejecutar la orden
```
rm -rf nombre-del-projecto/
```

# Añadir Git a un proyecto existente

## Situarte en el directorio que quieras desde la raiz

Si tienes un proyecto y este aún no está siendo versionado por Git. Para situarte desde cualquier punto en el que estés en el directorio que quieras:
```
cd ~/ruta/nombre-del-directorio-que buscas
```
En donde **~** es la raiz de mi usuario. P.E. Si mi carpeta se encuentra en Documents la ruta sería la siguiente 
```
cd ~/Documents/Nombre-de-la-carpeta/
```
## Inicializar Git

Para inicializar el uso de Git en ese proyecto y comenzar con el versionado utilizaremos el comando **init**
```
git init
```
Git inicialará un repositorio en esa carpeta, como working directory. Para ver que temos la carpeta **.git** que está oculta podemos listar todos los elementos dentro de esa carpeta, los visibles y los ocultos.
```
ls -al
```
## Añadir fichero

En este caso tenemos una carpeta con muchos ficheros, para añadir todos estos ficheros a la vez al **staging area** no necesitamos **add** añadirlos uno a uno. Para hacer esto lo realizamos mediante el siguiente comando.
```
git add . 
```
## Commit fichero

Lo único que nos falta es realizar nuestro primer commit de la manera que ya sabemos realizarlo
```
git commit -m "Mi prirmer commit"
```
## Eliminar repositorio

Ya estamos funcionando con un repositorio de git. Para dejar de tener versionado este proyecto lo único que tenmos que hacer es eliminar la carpeta **.git** de la carpeta para hacer esto basta con borrarla
```
rm -rf .git
```

# Trackear Archivos en Git

## Añadir cambios + mensaje para commit en la misma orden
Los pasos con ficheros para ser trackear ficheros en Git son:

1. Crear o modificar un fichero
2. Añadir **add** fichero para ser trackearlo / **Ahora este fichero está en el Staging Area**
3. Commiteamos el fichero / **Ahora este fichero se encuentra en el Local Ropository**

### Realizar estas dos últimas acciones a la vez

Para crear un fichero desde la terminal, *en mi caso uso Visual Studio Code*. Para lanzar visual solo hay que añadir *code*

```
code ruta/nombre-del-fichero.md
```

Con esto lanzamos un fichero nuevo con el nombre que le hemos dado dentro de visual. Añadimos contenido y guardamos el* fichero. Si ahora hacemos un **git status** veremos que tenemos un nuevo fichero y que este no ha sido añadido a *.git*

```
commit -am "mensaje que queremos para el commit"
```
## Ver listado de archivos trackeados

con la orden **ls-files** podemos ver el listado de ficheros que Git está trackeando

```
git ls-files
```

## Añadir ficheros paso a paso

1. Añadir ficheros **git add nombre-fichero.md**
2. Commitear fichero **git commit -m "mensaje para el commit"**

## Uso de add

Cada vez que usamos **add** estamos añadiendo cambios al Stagin Area, es la forma que tenemos de sumar cambios, todos los cambios que queremos. Con Commit estamos subiendo todos estos cambios a nuestro Local Repository. 

Podemos tener uno o varios documentos sin commitear a nuestro Local Repository y hacer cambios, cada uno de esos cambios los podemos añadir **add** al Staging Area sin que se suba aún nuestro fichero al repositorio local.

## Añadir ficheros y carpetas recursivamente

Si tengo varios niveles de carpetas, con varios ficheros dentro y los quiero añadir todos a la vez, **con add en la terminal solo te enseñará el primer nivel de carpetas**. Solo hay que utilizar la siguiente orden en la terminal.

```
git add .
```

Con esta orden, verás al hacer commit todo el listado de ficheros y carpetas que estarás añadiendo al repositorio local.

# Descartar Cambios

Al trabajar sobre **un mismo fichero esté puede tener diferentes versiones del mismo**:

1. Puede haber una versión en el repositorio local
2. Este también puede estar en Staging Area con una versión diferente


En esta página vamos a explicar cómo tener este escenario:

1. **Un fichero está commiteado en el Local Repository**

    ![Fichero commiteado en el Repositorio Local](assets/training/git/repository-git-repository.png)

2. **Hacemos nuevas modificaciones en ese mismo fichero**

3. **Añadimos estas nuevas modificaciones al Staging Area**

    ![Fichero en el Staging Area](assets/training/git/staging-area-git-repository.png)

4. **Queremos eliminar las morificaciones añadidas al Stagging Area**

    ![Git reset HEAD](assets/training/git/git-reset-head.png)

    ```
    git reset HEAD nombre-del-fichero.md
    ```
    
    Entonces el fichero vuelve a estar dentro del Working Directory

    ![Fichero en Working Directory](assets/training/git/working-directory-git-repository.png)

5. Recuperar el fichero commiteado al Local Ropository

    ![Git checkout --](assets/training/git/git-checkout.png)
    ```
    git checkout -- nombre-del-fichero.md

# Renombrar Ficheros

Para cambiar el nombre *rename* de un fichero debemos de usar
```
git mv nombre-del-fichero.md nuevo-nombre-del-fichero.md
```
Después del cambio de nombre commitear este cambio, antes de continuar con otros cambios, para estar seguros de que el cambio se ha producido correctamente.

## Rename fuera de Git

Podemos usar el mismo comando *mv* para hacer el cambio de nombre.

```
mv nombre-del-fichero.md nuevo-nombre-del-fichero.md
```

Tras este cambio fuera de Git hacemos un *git status* y vemos como para Git han ocurrido dos cosas:
1. El fichero renombrado ha sido eliminado
2. Existe un nuevo fichero sin añadir

![Rename Fuera de Git --](assets/training/git/rename-fuera-git.png)

Para poder controlar desde GIT estos cambios de nombre o de ficheros eliminados podemos hacer un *add* con el parámentro *-A* para que de forma recursiva esté controlando todos los cambios de nombre o archivos borrados que se incluyan.
```
git add -A
```
*mv* también sirve para mover ficheros en diferentes carpetas o niveles. En el siguiente ejemplo voy a mover un fichero a una carpeta llamada "folder"

```
git mv nombre-fichero.md folder
```

Al hacer un *git status* veremos que tenemos cambios en el staging area. Ahora voy a devolver el fichero a su nivel original.

```
git mv nombre-fichero.md ...
```

# Borrar Ficheros

1. Ejemplo de cómo borrar un fichero que aún no está siendo traqueado por Git. Para esto usaremos el comando *rm*
```
git rm nombre-fichero-a-borrar.md
```

2. Ejemplo de borrado de un fichero que ya está siendo traqueado por Git.
```
git rm nombre-fichero-a-borrar.md
```
El fichero ha sido borrado pero al hacer *git status* vemos cómo aún el borrado aún está en el *staging area* aún nos hace falta *commitear* la acción para que tenga efecto en *local repository*
```
git commit -m "borrado del fichero  nombre-fichero-a-borrar.md"
```
3. Ejemplo de borrar un fichero (solo en staged area), no hacer commit y recuperar fichero desde el *local repository*
```
git rm nombre-fichero-a-borrar.md
```
El borrado está en el *staging area* ahora queremos devolver el fichero al *working directory*
```
git restore --staged nombre-fichero-a-borrar.md
```
Aún nos falta recuperar el fichero de nuestro *local repository*
```
git checkout -- nombre-fichero-a-borrar.md
```

Ahora ya hemos recuperado el fichero que teníamos en nuestro *local repository*

# History
Devuelve la historia de commits en orden descendente

```
git log
```

Versión comprimida de la línea
```
git log --oneline --graph --decorate
```

Historia de commits delimitada por días
``` 
git log --since="3 days ago"
```

Historia de commits de un archivo en concreto
```
git log -- nombre-del-fichero.md
```

Historia de un commit *show* y añado el ID del commit que quiero ver
```
git show 895a6ce2029c64a4c2f5bb91a0e3380849c14d78
```

# Alias
Para comandos muy largos podemos crear *Alias* con la palabra que deseemos. para ello tenemos invocar config para crear el alias, en nuestro caso *hist* con la orden de git que queremos. En la orden que queremos de GIT, no incluimos la palabra GIT.

```
git config --global alias.hist "log --all --graph --decorate --oneline" git hist
```
Si abrimos el fichero *gitconfig* veremos que hemos escrito el alías con la orden de GIT
```
code ~/.gitconfig
```
```
[alias]
	hist = log --all --graph --decorate --oneline
```
### Resumen de comandos
```
pwd
cd projects/starter-web
ls
git status
clear
git log --all --graph --decorate --oneline
git hist
git config --global alias.hist "log --all --graph --decorate --oneline" 
git hist
clear
code ~/.gitconfig
git hist
mate ~/.gitconfig
git hist
clear
```
# Ignorar Ficheros
Para ver todos los ficheros y carpetas

```
ls -al
```
Para que GIT no tenga en cuenta fichero podemos crear un fichero especial llamado *gitignore*

Dentro de este fichero podemos obviar tres tipos de elementos:
1. Ficheros específicos: 
```
nombre-fichero.md
```
2. Ficheros con una extensión específica: 
```
*.ext
```
3. Carpetas :
```
nombre-carpeta/
```
Si no existe el fichero *gitignore* lo creamos
```
code .gitignore
```

# Trabajar con Ramas

## Listar ramas

Para conocer todas las ramas que existen en el local y en el repositorio remoto.

```
git branch -a
```

![git branch -a las ramas en local y remoto](assets/training/git/git-branch-a.png)

La rama en local en la que te encuentras se marca con asterisco.

### Para listar solo las ramas locales

```
git branch
```

## Crear nueva rama

El comando para crear una nueva rama es el siguiente:

```
git branch nombre-rama
```

Con esto aún no estamos en la rama que hemos creado. Para movernos a la nueva rama tenemos que utilizar el comando **checkout**

```
git checkout nombre-rama
```

## Renombrar ramas

Para cambiar el nobre de una rama a otra
```
git branch -m nombre-rama nuevo-nombre-rama
```

## Borrar ramas

```
git branch -d nombre-rama-borrar
```

Master no se puede borrar y tienes que estar en una rama diferente a la que quieres borrar para poder borrarla.

## Crear y moverse a una rama en un solo paso

Para realizar los pasos de crear una rama y movernos a la nueva rama que acabamos de crear podemos realizar el atajo de:

```
git checkout -b nombre-rama
```