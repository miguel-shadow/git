**Contenidos**

- [1. Estados Git](#1-estados-git)
    - [1.1. Working Directory](#11-working-directory)
    - [1.2. Staging Area](#12-staging-area)
    - [1.3. Repository](#13-repository)
- [2. Comandos](#2-comandos)
    - [2.1. Inicializar un repositorio](#21-inicializar-un-repositorio)
    - [2.2. Ficheros y carpetas modificados (Working Directory)](#22-ficheros-y-carpetas-modificados-working-directory)
        - [2.2.1. Ver diferencias](#221-ver-diferencias)
        - [2.2.2. Revertir cambios](#222-revertir-cambios)
    - [2.3. Añadir los cambios (Staging Area)](#23-añadir-los-cambios-staging-area)
        - [2.3.1. Ver diferencias](#231-ver-diferencias)
        - [2.3.2. Resetear cambios](#232-resetear-cambios)
    - [2.4. Commit (Repository)](#24-commit-repository)
        - [2.4.1. Ver commits](#241-ver-commits)
        - [2.4.2. Mostrar cambios de un commit](#242-mostrar-cambios-de-un-commit)
        - [2.4.3. Regresar a un commit](#243-regresar-a-un-commit)
    - [2.5. Cambios temporales (Stash)](#25-cambios-temporales-stash)
        - [2.5.1. Añadir](#251-añadir)
        - [2.5.2. Listar cambios y ver detalles](#252-listar-cambios-y-ver-detalles)
        - [2.5.3. Regresar](#253-regresar)
    - [2.6. Ramas (Branch)](#26-ramas-branch)
        - [2.6.1. Ver ramas](#261-ver-ramas)
        - [2.6.2. Crear rama](#262-crear-rama)
        - [2.6.3. Eliminar rama](#263-eliminar-rama)
        - [2.6.4. Renombrar rama](#264-renombrar-rama)
        - [2.6.5. Cambiar de rama](#265-cambiar-de-rama)
        - [2.6.6. Mergear ramas](#266-mergear-ramas)
        - [2.6.7. Ver último commit de la rama](#267-ver-último-commit-de-la-rama)
        - [2.6.8. Rebase](#268-rebase)
        - [2.6.9. Cherry pick](#269-cherry-pick)
    - [2.7. Repositorios remotos](#27-repositorios-remotos)
        - [2.7.1. Ver enlace remoto](#271-ver-enlace-remoto)
        - [2.7.2. Enlazar repositorio local con remoto](#272-enlazar-repositorio-local-con-remoto)
        - [2.7.3. Clonar un repositorio remoto](#273-clonar-un-repositorio-remoto)
        - [2.7.4. Actualizar cambios remotos](#274-actualizar-cambios-remotos)
        - [2.7.5. Sincronizar cambios locales](#275-sincronizar-cambios-locales)
        - [2.7.6. Publicar una rama](#276-publicar-una-rama)
        - [2.7.7. Pull request](#277-pull-request)
- [3. Git Ignore](#3-git-ignore)
    - [3.1. Eliminar rastreo](#31-eliminar-rastreo)
- [4. Git config](#4-git-config)
    - [4.1. User](#41-user)
    - [4.2. Safe](#42-safe)
    - [4.3. Alias](#43-alias)
    - [4.4. Configuración personal](#44-configuración-personal)
- [5. SSH](#5-ssh)


# 1. Estados Git


## 1.1. Working Directory
Se refiere a los **archivos y carpetas** locales en los que se realizan modificaciones


## 1.2. Staging Area
Se refiere a una **copia de los cambios realizados** en los archivos locales que serán incluidos en el repositorio


## 1.3. Repository
Se refiere al **código modificado** y **sincronizado** con el repositorio local


# 2. Comandos
Se puede ver la ayuda de los comandos desde la terminal mediante la flag `-h` o `--help`:

```bash
git <comando> -h # Se visualiza en la terminal
git <comando> --help # Se visualiza en el navegador
```


## 2.1. Inicializar un repositorio
Para inicializar un repositorio local se debe abrir una terminal e introducir el siguiente comando:

```bash
git init
```

Se creará una carpeta `.git` que almacenará la configuración y los datos del repositorio


## 2.2. Ficheros y carpetas modificados (Working Directory)
Se pueden ver todos los ficheros o carpetas que has sido modificados (nuevos, editados, eliminados...) mediante el siguiente comando:

```bash
git status
```

El estado de *Git* es ***Working Directory***


### 2.2.1. Ver diferencias
El comando anterior solo muestra el listado de archivos y carpetas modificados. Para ver esas modificaciones archivo por archivo, se utiliza el comando:

```bash
git diff # Muestra las diferencias de todos los archivos
git diff <path_fichero_carpeta> [<fichero_carpeta_2> ...] # Muestra las diferencias del archivo/s especificado/s
```


### 2.2.2. Revertir cambios
Para revertir los cambios de un fichero o carpeta modificados, se utiliza el comando:

```bash
git checkout -- <path_fichero_carpeta> [<fichero_carpeta_2> ...]
```


## 2.3. Añadir los cambios (Staging Area)
Para añadir los cambios realizados (estado *Git* ***Working Directory***), se utiliza el comando:

```bash
git add <path_fichero_carpeta> <fichero_carpeta_2> # Añade los ficheros manualmente
git add . # Añade todos los ficheros nuevos o modificados # Añade todos los ficheros nuevos, modificados o eliminados
git add *.<extension> # Añade todos los archivos de una extensión (se puede utilizar para carpetas, rutas, nombre contenido...)
```

El estado *Git* sería ***Staging Area***


### 2.3.1. Ver diferencias
Se pueden ver los cambios realizados en los archivos utilizando el comando:

```bash
git diff # Muestra los cambios de todos los archivos
git diff <path_fichero_carpeta> [<fichero_carpeta_2> ...] # Muestra los cambios del archivo/s especificado/s
git diff --staged # se pueden ver los cambios de los archivos staged respecto del último commit
```


### 2.3.2. Resetear cambios
Se pueden resetear todos los cambios añadidos y que aún no han sido *commiteados*. Para ello se utiliza el comando:

```bash
git reset HEAD <path_fichero_carpeta>
```


## 2.4. Commit (Repository)
Para aplicar los cambios realizados en el repositorio local (el estado *Git* cambiaría a ***Repository***), se utiliza el comando:

```bash
git commit
git commit -m "<mensaje>" # Permite añadir el mensaje del commit directamente, sin hacerlo desde el editor
```

> [!IMPORTANT]
> Para realizar el *commit*, es obligatorio introducir un **mensaje** en el editor que se abre.
>
> Para guardar y salir del editor ***VIM*** (editor predeterminado en *Git Bash*), pulsar la tecla `ESC` y escribir `:wq`

> [!TIP]
> Con el comando:
>
> ```bash
> git commit --amend -m "<mensaje>"
>```
>
> Se puede modificar el mensaje del último *commit* o añadir nuevos cambios a ese commit


### 2.4.1. Ver commits
Se puede visualizar todos los *commits* realizados. Se muestran de más reciente a más antiguo. Cada *commit* posee un **hash** identificativo único. Para ello, se ejecuta el comando:

```bash
git log
git log -n <numero> # Muestra los últimos N commits
git log --oneline # Muestra los commits en una línea
git log --graph # Muestra el gráfico de las ramas con los commits
```

> [!TIP]
> Hay numerosos formatos y se pueden combinar entre ellos


### 2.4.2. Mostrar cambios de un commit
Para ver los cambios realizados en un *commit*, mostrando el hash del *commit* y sus modificaciones se utiliza el comando:

```bash
git show # Muestra los cambios del último commit
git show <hash_commit> # Muestra los cambios del commit especificado
```


### 2.4.3. Regresar a un commit
Se pueden **deshacer** los cambios *commiteados* mediante distintos métodos:

```bash
git revert <hash_commit_a_deshacer> # Deshace el commit indicado, pero no se elimina del historial, si no que crea un nuevo commit con los cambios deshechos

git reset --soft <hash_commit_a_regresar> # Deshace los commits posteriores, eliminándolos del historial, pero mantieniendo las modificaciones en el staging area

git reset --hard <hash_commit_a_regresar> # Deshace los commits posteriores, eliminándolos del historial y eliminando las modificaciones
```

> [!TIP]
> Se puede **sobrescribir** el **historial** de la rama del servidor remoto mediante:
>
> ```bash
> git push --force origin <nombre_rama>
>```
>
> Para **recibir** el nuevo **historial** desde un equipo que tiene los cambios deshechos sin deshacer, se debe ejecutar:
>
> ```bash
> git fetch origin
> git reset --hard origin/<nombre_de_rama>
>```


## 2.5. Cambios temporales (Stash)
Se pueden almacenar **cambios temporales** sin necesidad de hacer un commit o, ni si quiera de realizar un `git add`


### 2.5.1. Añadir
Para ello existe el comando:

```bash
git stash
git stash -u # Almacenar cambios temporalmente en archivos no traqueados por Git
```


### 2.5.2. Listar cambios y ver detalles
Se pueden almacenar distintos cambios temporales con los comandos anteriores. Se almacenan en una pila, es decir, el índice 0 es el último cambio almacenado, para listar los cambios temporales almacenados, se utiliza el comando:

```bash
git stash list
```

Se pueden ver los detalles de los cambios temporales con los comandos:

```bash
git stash show
git stash show -p # Muestra más detalles
```

> [!TIP]
> Se puede elegir que *stash* visualizar añadiendo el índice deseado al final del comando.
>
> Para mostrar los archivos no *trackeados*, se debe añadir la *flag* `-u`


### 2.5.3. Regresar
Para regresar los cambios temporales, se debe utilizar los comandos:

```bash
git stash pop # Último cambio almacenado
git stash pop <numero_indice> # Elegir mediante el índice
```


## 2.6. Ramas (Branch)
Las ramas son divisiones del código para trabajar de manera paralela


### 2.6.1. Ver ramas
Mostrar las ramas existentes:

```bash
git branch
```

> [!NOTE]
> La **rama** en la que estemos **actualmente** se marca con un asterisco `*<nombre_rama_seleccionada>`

> [!TIP]
> Con la flag `-r` se muestran las ramas remotas. Con `-a` se muestran todas las ramas, tanto locales como remotas


### 2.6.2. Crear rama
Para crear una rama se utiliza el comando:

```bash
git branch <nombre_rama>
```


### 2.6.3. Eliminar rama
Si se desea eliminar una rama existente, se ejecuta el comando:

```bash
git branch -d <nombre_rama>
```

> [!CAUTION]
> Se debe estar situado en una **rama distinta** a la que se va a eliminar


### 2.6.4. Renombrar rama
Se puede renombrar una rama existente mediante el comando:

```bash
git branch -m <nombre_anterior> <nombre_nuevo>
```


### 2.6.5. Cambiar de rama
Para cambiar de una rama a otra, se puede utilizar el comando:

```bash
git checkout <nombre_rama>
git switch <nombre_rama>
```

> [!IMPORTANT]
> `checkout` realiza más acciones además del cambio de rama. Actualmente se recomienda utilizar `switch`

> [!TIP]
> Crear una nueva rama y cambiarse de manera automática:
>
> ```bash
> git checkout -b <nombre_rama_nueva>
> git switch -c <nombre_rama_nueva> # Recomendada
> ```
>
> Para ahcer un cambio rápido (*toggle*) entre la rama actual y la rama anterior:
>
> ```bash
> git switch -
> ```


### 2.6.6. Mergear ramas
Un ***merge*** es la unión de una rama en otra, es decir, los cambios realizados en una rama son insertados en la otra. Para ello, debemos **situarnos** en la **rama** en la que **queremos introducir** los cambios de la otra rama y ejecutar el comando:

```bash
git merge <nombre_rama_con_cambios>
```

> [!IMPORTANT]
> Si la **rama principal** no ha tenido ningún cambio, al mergear la rama con los cambios, es recomendable utilizar la flag `--no-ff` para crear un commit de fusión y evitar el ***Fast-Forward merge*** (se muestran los commits de la otra rama como si se huiesen realizado en la rama principal)

> [!TIP]
> Con la flag `--no-commit` añade los cambios al *staging area* y se debe realizar el *commit* manualmente

> [!NOTE]
> Una vez realizado el merge, se suele **eliminar** la otra rama. La secuencia de comandos comúnmente utilizada es:
>
> ```bash
> git checkout <rama_sin_cambios> # Cambiar a la rama sin cambios
> git merge <rama_con_cambios> # Insertar los cambios de la otra rama
> git branch -d <rama_con_cambios> #Eliminar la otra rama
> ```


### 2.6.7. Ver último commit de la rama
Se puede ver el **hash** y el **mensaje** del **último commit** realizado en la rama con el comando:

```bash
git branch -v
```


### 2.6.8. Rebase
Es una acción similar a *mergear*, pero en lugar de fusionar los cambios, se **aplican** los ***commits*** de una rama en otra. De esta manera se mantiene un historial más limpio y lineal, pero se pierde la trazabilidad. El comando es:

```bash
git rebase <nombre_rama_con_cambios>
```

> [!WARNING]
> ***Rebase*** reescribe el historial de la rama, siendo peligroso si la rama ha sido compartida con otros usuarios


### 2.6.9. Cherry pick
Se puede aplicar un commit específico de una rama en otra rama, sin necesidad de mergear la rama completa. Para ello, existe el comando:

```bash
git cherry-pick
```

> [!TIP]
> Con la flag `--no-commit` añade los cambios al *staging area* y se debe realizar el *commit* manualmente

> [!TIP]
> Se pueden aplicar varios commits seguidos:
>
> ```bash
> git cherry-pick <hash_1> <hash_2>
> ```
>
> O un rango:
>
> ```bash
> git cherry-pick <hash_inicial>^..<hash_final>
> ```


## 2.7. Repositorios remotos
Hasta ahora solo se estaba trabajando en repositorios locales. Para poder trabajar con más personas en un mismo repositorio, es necesario utilizar repositorios remotos como ***[GitHub](https://github.com/)***, *[GitLab](https://gitlab.com/)*, *[Bitbucket](https://bitbucket.org/)*...

Dependiendo de la plataforma, se siguen distintos pasos para crear un repositorio. En ***GitHub*** se puede crear de dos maneras:

- Repositorio **sin** contenido: El repositorio se crea, pero debe ser **enlazado** con un repositorio local o introducir un contenido (archivo o carpeta) para que se **inicialice**
- Repositorio **con** contenido: El repositorio se crea **inicializado**, es decir, puede ser **clonado** (descargado) en local


### 2.7.1. Ver enlace remoto
Para ver a qué enlace remoto está apuntando un repositorio:

```bash
git remote -v
```


### 2.7.2. Enlazar repositorio local con remoto
Para enlazar un repositorio local con un repositorio vacío, se utiliza el comando:

```bash
git remote add origin <enlace_repositorio>
```

> [!TIP]
> Para **cambiar** el enlace del repositorio
>
> ```bash
> git remote set-url origin <enlace_repositorio>
> ```


### 2.7.3. Clonar un repositorio remoto
Si el repositorio remoto posee contenido, se debe clonar en local para adquirirlos. Para ello, se utiliza el comando:

```bash
git clone <enlace_repositorio>
```


### 2.7.4. Actualizar cambios remotos
Si se ha producido algún cambio en el repositorio remoto, existen varias formas de adquirir esos cambuos en el repositorio local:

```bash
# Obtener los cambios e insertarlos manualmente
git fetch # Obtener los cambios remotos
git merge origin/<rama_remota> # Mergear los cambios en el repositorio local

# Obtener los cambios e insertarlos directamente
git pull
```


### 2.7.5. Sincronizar cambios locales
En cambio, para sincronizar los cambios locales en el repositorio remoto, se debe realizar el comando:

```bash
git push
```

> [!IMPORTANT]
> Antes de ejecutar el comando, se debe haber añadido los cambios locales al *Staging Area* (`git add`) y haber realizado el *commit* correspondiente (`git commit`)

> [!TIP]
> Se puede sobreescribir el historial del rempositorio remoto mediante:
>
> ```bash
> git push --force
> ```


### 2.7.6. Publicar una rama
Se puede publicar una rama creada localmente en el repositorio remoto, para ello se utiliza el comando:

```bash
git push origin <nombre_rama>
```


### 2.7.7. Pull request
Permiten **revisar** el código antes de mergear los cambios de una rama a otra, evitando errores de código, falta de documentación, etc. Para ello, en vez de mergear en local y realizar un *push*, se **publica** la **rama** con los **cambios**. Posteriormente, en cada servidor *Git* existe un apartado de ***Pull request*** (*PR*).

La ***PR*** se puede:

- **Aceptar**: Los cambios de la rama publicada **se mergean** a la rama principal
- **Rechazar**: El merge **no** se **completa** y se **cierra** la PR (se puede volver a abrir con nuevos cambios)


# 3. Git Ignore
Se puede crear un archivo llamado `.gitignore` para decidir qué archivos o directorios **no deben** ser **rastreados** por Git en el repositorio:

Existen numerosas formas de especificar archivos y carpetas:

- `<nombre>.<extension>`: No rastrea el archivo exacto
- `*.<extension>`: No rastrea ningún archivo que tenga esa extensión
- `<nombre>/*`: No rastrea una carpeta y su contenido
- `*<nombre>*`: No rastrea archivos y carpetas que contengan `<nombre>` en el nombre
- `<nombre>*`: No rastrea archivos y carpetas que comiencen por `<nombre>`
- `*<nombre>.<extension>`: No rastrea archivos y carpetas que finalicen en `<nombre>` y tengan la extensión `<extension>`
- [Más información](https://github.com/github/gitignore)

> [!TIP]
> Se pueden crear varios archivos `.gitignore` en distintas rutas de un mismo repositorio. Cada archivo tiene efecto en la carpeta donde se encuentra y en las subcarpetas de ésta. Generalmente se utiliza un único `.gitignore` en la raíz del repositorio


## 3.1. Eliminar rastreo
Si se desea que un archivo rastreado sea **ignorado** (pero **no eliminarlo** localmente), se añade al `.gitignore` y se ejecuta el comando:

```bash
git rm --cached <nombre_archivo>
```


# 4. Git config
*Git* posee **distintas configuraciones** que permiten personalizar su funcionamiento. La configuración **global** (afecta en todos los repositorios) se almacena en `%USERPROFILE%\.gitconfig` en *Windows*, pero cada repositorio puede tener su propia **configuración individual** (`.git\config`).

Se puede ver el **listado** de configuraciones aplicadas mediante los comandos:

```bash
git config --list # Muestra toda la configuración
git config --list --local # Muestra la configuración individual del repositorio
git config --list --global # Muestra la configuración global
git config --list --system # Muestra la configuración del sistema
```

> [!IMPORTANT]
> Las configuraciones se **sobrescriben** de **arriba** hacia **abajo**, es decir, si existen dos configuraciones con diferentes valores, se aplicará la configuración que se encuentra más abajo del listado

> [!TIP]
> La configuración se puede realizar mediante la edición del archivo correspondiente (repositorio individual o global) o mediante comandos:
>
> ```bash
> git config user.name "<nombre>"
> git config user.email <correo_electronico>
> ...
> ```
>
> Mediante la *flag* `--global` las configuraciones se almacenan en el archivo `.gitconfig` del usuario (global)


## 4.1. User
Permite elegir el nombre y el correo del usuario que realiza los cambios

```ini
[user]
    email = <correo_electronico>
    name = <nombre>
```


## 4.2. Safe
Permite añadir directorios seguros para poder ejecutar comandos git

```ini
[safe]
    directory = "<path>/<al_directorio>"
    directory = "<otro_path>/<al_directorio_2>"
    directory = * # Todos los directorios se consideran seguros
```


## 4.3. Alias
Se pueden crear **alias** para ejecutar comandos de Git. Se pueden utilizar para ejecutar comandos con varias flags o múltiples comandos

Algunos alias útiles son:

```bash
git config --global alias.logDetails "log --oneline --graph --decorate --all" # Muestra el historial de commits con detalles
git config --global alias.addAll "add ." # Añade todos los cambiós al *staging area*
git config --global alias.toggle "switch -" # Cambia a la rama anterior
git config --global alias.addCommit '!f() { git add . && git commit -m "$1"; }; f' # Añade los cambios y crea un commit con el mensaje introducido `git addCommit "<mensaje>"`
```

> [!IMPORTANT]
> Para eliminar un alias, se puede ejecutar el comando:
>
> ```bash
> git config --global --unset alias.<nombre_alias>
> ```
>
> O sobreescribir el archivo de configuración

> [!TIP]
> Para ver los alias existentes, ejecutar
>
> ```bash
> git config --get-regexp alias
> ```


## 4.4. Configuración personal

```ini
[user]
    email = <correo_electronico>
    name = <nombre>
[filter "lfs"]
    required = true
    clean = git-lfs clean -- %f
    smudge = git-lfs smudge -- %f
    process = git-lfs filter-process
[safe]
    directory = *
[core]
    editor = code --wait
[help]
    autocorrect = 50
[alias]
    logDetails = log --oneline --graph --decorate --all
    addAll = add .
    toggle = switch -
    addCommit = "!f() { git add . && git commit -m \"$1\"; }; f"
```


# 5. SSH
Se puede trabajar con repositorios a través de **SSH** en vez de un enlace HTTPS. Permiten trabajar con repositorios **sin** la necesidad de **introducir credenciales**. Para ello se conecta al servidor Git mediante claves SSH. Se puede **retirar el acceso** de las claves en cualquier momento.

Pasos a realizar en Windows:

1. **Generar claves SSH**: Existen numerosas formas de generar claves SSH mediante herramientas como ***openSSH***, ***openSSL***, ***BitWarden***... A continuación se explica como hacerlo mediante `ssh-keygen` (viene instalado con *Git Bash*):
    - Ejecutar el **comando** `ssh-keygen.exe` para **crear** un par de claves SSH (una pública y otra privada)
        - Solicita el **nombre** de los **archivos**
        - Solicita una **contraseña** (se puede dejar vacía, no recomendado en equipos no seguros)

1. **Copiar la clave pública** (`.pub`) en el **repositorio** remoto (*GitHub*, *GitLab*...):
    - En ***GitHub***: `Settings` → `SSH and GPG keys` → `New SSH key` → `Copiar el contenido de la clave pública`

1. **Modificar** el archivo `config` en la carpeta `%USERPROFILE%\.ssh` (Si no existe la carpeta, se debe crear)

    ```bash
    Host github-<nombre> # Nombre personalizado
      HostName github.com
      User git
      IdentityFile <path/clave_privada> # Generalmente ~/.ssh/<clave_privada>
      IdentitiesOnly yes
    ```

1. **Clonar** un repositorio: Se debe copiar el enlace de **SSH** (*No el de HTTPS*) del repositorio. Antes de ejecutar el comando `git clone`, se debe cambiar el dominio (en este caso `github.com`) por el **Host** almacenado en `.ssh/config`:

    ```bash
    git clone git@github-<nombre>:path/repositorio.git
    ```


> [!TIP]
> Para **añadir otra cuenta**, se deben repetir los pasos anteriores, cambiando el `<nombre>` en `Host` del archivo `.ssh/config` por otro y **enlazándolo** con la clave privada correspondiente.
>
> Mediante `github-<nombre>` al realizar el *clone*, se puede **elegir** con que **cuenta** se desea clonar el repositorio, muy útil en los repositorios privados
