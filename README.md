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



#### `git restore `
