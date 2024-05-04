# CURSO GIT - SCESI

## Clase 1

### `git init`

El comando `git init` se utiliza para iniciar un nuevo repositorio Git en un directorio local. Este comando crea un nuevo subdirectorio llamado `.git` que contiene todos los archivos necesarios para el repositorio.

#### Uso:
    git init

---

### `git add`

El comando `git add`  se utiliza para agregar cambios de archivos al área de preparación (staging area) para el próximo commit en Git. 
> Básicamente, nos permite decir a Git qué cambios deseas incluir en tu próximo commit.
#### Usos, ejemplos y variante:

1. Agregar un archivo específico al área de preparación:

    `git add nombre_archivo.txt`
2. Agregar todos los archivos modificados al área de preparación:

    `git add .`

3. Agregar cambios parciales o por líneas utilizando git add -p:

    `git add -p`

4. Agregar un directorio completo al área de preparación:

    `git add nombre_directorio/`

---
### `git commit`

[que significa commit?](https://es.wikipedia.org/wiki/Commit)

El comando `git commit`  se utiliza para crear un nuevo commit en Git, que representa un conjunto de cambios en tu repositorio. Aquí tienes algunos ejemplos de cómo usar git commit:
#### Uso, ejemplo y variantes:

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
