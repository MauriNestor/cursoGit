# CURSO GIT - SCESI

## Clase 1

## Estados en Git

### Modificado (Modified):
Este es el estado en el que se encuentran los archivos que han sido modificados en tu directorio de trabajo desde el último commit. Estos cambios aún no se han preparado para el próximo commit.

>en vscode se lo representa con una **M**:

![modified](/imagenes/M.png)


### Preparado (Staged o Staging Area):
También conocido como "staging area", este es el estado intermedio donde se preparan los cambios antes de realizar un commit. Los archivos en este estado han sido marcados para ser incluidos en el próximo commit, pero aún no se han confirmado definitivamente en el historial del repositorio.

>en vscode se lo representa con una **U** antes de ser agredado

![Staged o Staging Area](/imagenes/U.png)

>en vscode se lo representa con una **A** despues de ser de ser agregado con git add:

![Staged o Staging Area](/imagenes/A.png)


### Confirmado (Committed):
Este es el estado final y más estable de tus archivos, donde se almacenan los commits confirmados en tu repositorio. Los archivos en este estado representan una versión estable de tu proyecto en un momento específico en la historia del repositorio.

>en vscode se lo representa con una **ninguna letra(desaparecen las demas)**:

#### `que es HEAD?`
- es un puntero especial que indica la ubicación actual en el historial de commits del repositorio. 
- Señala al commit en el que se esta trabajando

![Staged o Staging Area](/imagenes/head.png)

- con el comando `git log --online` se identifica en donde esta el HEAD con facilidad.
![Staged o Staging Area](/imagenes/headCap.png)

### Comandos troncales

#### `git init`

El comando `git init` se utiliza para iniciar un nuevo repositorio Git en un directorio local. Este comando crea un nuevo subdirectorio llamado `.git` que contiene todos los archivos necesarios para el repositorio.

##### Uso:
    git init

---

#### `git add`

El comando `git add`  se utiliza para agregar cambios de archivos al área de preparación (staging area) para el próximo commit en Git. 
> Básicamente, nos permite decir a Git qué cambios deseas incluir en tu próximo commit.
##### Usos, ejemplos y variante:

1. Agregar un archivo específico al área de preparación:

    `git add nombre_archivo.txt`
2. Agregar todos los archivos modificados al área de preparación:

    `git add .`

3. Agregar cambios parciales o por líneas utilizando git add -p:

    `git add -p`

4. Agregar un directorio completo al área de preparación:

    `git add nombre_directorio/`

---
#### `git commit`

[que significa commit?](https://es.wikipedia.org/wiki/Commit)

El comando `git commit`  se utiliza para crear un nuevo commit en Git, que representa un conjunto de cambios en tu repositorio. Aquí tienes algunos ejemplos de cómo usar git commit:
##### Uso, ejemplo y variantes:

1. Realizar un commit con un mensaje simple

    `git commit -m "Mensaje del commit"`
2. Incluir todos los cambios realizados en el commit:

    `git commit -a -m "Mensaje del commit"`

3. Editar el mensaje del último commit:
    `git commit --amend`

4. Realizar un commit sin agregar archivos explícitamente:
    `git commit -m "Mensaje del commit" --only`
    >Este comando realiza un commit únicamente con los archivos que ya están en el área de preparación, omitiendo cualquier archivo que no haya sido previamente agregado con git add.


## RESUMEN GRAFICO DE COMO FUNCIONA GIT INIT, ADD y COMMIT
![Grafico de 3 comandos basicos](/cursoGit/imagenes/gitclase1.png "Resumen grafico")

### Comandos Utiles

#### `git status `
 se utiliza para obtener información sobre el estado actual del repositorio Git. 
 1. **Ver archivos modificados:** git status muestra una lista de los archivos que han sido modificados en tu directorio de trabajo desde el último commit.
 2. **Ver archivos en el área de preparación:** Muestra los archivos que han sido agregados al área de preparación (staging area) y que están listos para ser incluidos en el próximo commit.
3. **Ver archivos no rastreados:** git status también muestra los archivos que aún no han sido rastreados por Git y que no forman parte del control de versiones.

#### `git log `
se utiliza para mostrar el historial de commits en un repositorio Git. Proporciona una lista detallada de los commits que han ocurrido en la rama actual, comenzando desde el commit 

1. Ver el historial de commits completo:
    `git log`
2. Ver el historial de commits con un formato resumido:
    `git log --oneline`
3. Ver el historial de commits de un archivo específico:
    `git log nombre_archivo`

4. Ver el historial de commits de un autor específico:
    `git log --author="nombre_autor"`

5. Ver el historial de commits de una rama específica:
    `git log nombre_rama`


---

## Clase 2

### Ramas

> **que es una rama?** ->  línea de desarrollo independiente que permite trabajar en funcionalidades, correcciones de errores o experimentos sin afectar la rama principal del proyecto

#### funcion de una rama
- Desarrollo paralelo

### Maneras de crear una rama

1. Crear una rama y cambiar a ella de inmediato: `git checkout -b nueva_rama`
2. Crear una rama sin cambiar a ella `git branch nueva_rama`
3. Crear una rama basada en otra rama: `git checkout -b nueva_rama rama_base`
4. Crear una rama apartir de un commit en especifico `Crear una nueva rama desde un commit específico:`

### Navegar entre ramas
- Cambiar a una rama específica: `git checkout nombre_rama`
- Cambiar a la última rama utilizada: `git checkout -`

### Borrar ramas
- borrar una rama que ya a sido fusionada con la rama que estamos ejecutando: `git branch -d <nombre_rama>`
- Forzar la eliminación de una rama si aun no se fusiono con otra `git branch -D nombre_rama`
### Podar ramas 
- ver que ramas de borrarian en el repo remoto llamado origin, útil para ver qué referencias se eliminarían sin realizar realmente ninguna acción de eliminación.
`git remote prune origin --dry-run`
- para eliminar todas las ramas que no sean necesarias: `git remote prune`
> **tip**: Cuando se elimina una rama en el repositorio remoto, Git no la eliminará automáticamente de tu repositorio local. Esto puede dejar referencias locales a ramas que ya no existen en el repositorio remoto.

---
## Clase 3

#### `git restore `
 restaurar archivos en el directorio de trabajo o en el área de preparación a un estado específico, ya sea deshaciendo cambios no deseados o revirtiendo archivos a una versión anterior.

#### Usos
1. Restaurar un archivo en el directorio de trabajo a su estado previo al último commit: `git restore nombre_archivo`
2. Restaurar un archivo a una versión específica: `git restore --source=commit_hash nombre_archivo`
3. Restaurar un archivo eliminado: `git restore --source=commit_hash --staged nombre_archivo_eliminado`
4. Restaurar un archivo en el área de preparación a su estado previo al último commit:`git restore--staged nombre_archivo`

## Clase 4

### **Un poco de conceptos/teoria**

#### forks
- copia de un repositorio en el que cualquier usuario puede trabajar de forma independiente.
Son usados para contribuir proyectos de otras personas.
#### Acciones
- Se usa git hub actions para compilar, probar, desplegar y publicar tu código de forma automatizada.
#### Issues
- 
#### claves ssh
- se utilizan para autenticar la identidad de un usuario en un sistema remoto de forma segura
- Consisten en una clave pública y una clave privada. 
- para crear estas claves:
`ssh-keygen -t rsa -b 4096 -C "tu_correo_electronico@example.com"`
#### git remote
-  administrar conexiones remotas a repositorios
##### Usos
1. Enlaza un nuevo repo remoto con el nombre especificado y la URL proporcionada:
`git remote add <nombre> <URL>`
2. Elimina la conexión remota con el nombre especificado: `git remote remove origin`
3. Cambia el nombre de una conexión remota de <nombre_viejo> a <nombre_nuevo>
`git remote rename origin upstream`
4. Muestra una lista de todas las conexiones remotas junto con sus URL: `git remote -v`
5. Muestra información detallada sobre la conexión remota: `git remote show origin`
6. Elimina referencias locales a ramas remotas que ya no existen en el servidor remoto:
`git remote prune origin`


creando rama remota
git fetch   
git clone 

git revert 
git reset