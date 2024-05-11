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
![Grafico de 3 comandos basicos](/imagenes/gitclase1.png "Resumen grafico")

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


### Fusionar ramas `git merge`
- Se usa para incorporar cambios de una rama a la rama en la que ejecutamos el comando.
![git merge](/imagenes/merge.png)
### Usos y variantes
1. Fusionar una rama secundaria en la rama actual: `git merge feature-branch`
- Modificando el mensaje de commit
- Abre el editor antes de hacer el commit: `git merge --edit`
- Evita que haga commit automáticamente: `git merge --no-commit`

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
### `git push`
se utiliza para enviar cambios locales confirmados a un repositorio remoto. 
#### Usos y variantes
1. Para enviar los cambios locales de una rama específica al repositorio remoto:`git push origin nombre_rama`
2. Si queremos enviar los cambios locales a una rama específica del repositorio remoto, pero queremos que la rama remota tenga un nombre diferente:
`git push origin nombre_rama_local:nombre_rama_remota`
3. Configura la rama local para que haga un seguimiento de la rama remota después de enviar los cambios.
`git push -u origin nombre_rama`
4. forzar la actualizacion de una rama: `git push --force origin nombre_rama`
5. envia todas las ramas locales al remoto: `git push --all origin`
6. envia todas las etiquetas locales al repo remoto: `git push --tags origin`
7.  Realiza una simulación de la operación de push: `git push --dry-run origin nombre_rama`

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
- herramienta que permite realizar un seguimiento de tareas, problemas, ideas
#### claves ssh
- se utilizan para autenticar la identidad de un usuario en un sistema remoto de forma segura
- Consisten en una clave pública y una clave privada. 
- para crear estas claves:
`ssh-keygen -t rsa -b 4096 -C "tu_correo_electronico@example.com"`
#### `git remote`
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

### Algunos comandos utiles(parte 2)
#### `creacion de ramas remotas`
1. primero se debe crear una rama en la repo local
2. confirmarlos
3. enviar la rama al repo remoto: `git push origin nueva_rama`

#### `git clone` 
- se utiliza para crear una copia local de un repositorio Git remoto.
`git clone <URL_del_repositorio_remoto> [<nombre_de_directorio_local>]`

#### `git fetch` 
- actualiza tu repositorio local con la información más reciente del repositorio remoto
`git fetch <nombre_remoto>`

## Algunas preguntas curiosas
> hacer push desde una rama secundaria a la main, no hara nada?

- No, porque se hace una asignacion de uno a uno, esto quiere decir que no hay la posibilidad 
de modoficar una rama en la nube desde una rama local diferente

> hay alguna manera de hacerlo?
- si, haciendo el siguiente comando: git push login origin login: main (considerado peligroso)

## Clase 5

### Flujos de trabajo y estrategias de ramas en Git
- Todas las estrategias se basan esencialmente en la forma en la que vas a tratar de crear (o no) ramas y fusionarlas a la rama principal.

#### GIT FLOW
##### Ramas Principales
Se basa en la creacion de 2 ramas, la main(produccion) y la develop(donde se hacen las nuevas funciones para produccionn)Solo esta rama
develop puede hacerse el merge a la main 
![gitflow](/imagenes/gitflow.png)

##### Ramas de Apoyo
Ramas temporales que seran eliminadas, una vez q sean fucionadas.
- **Feature**: Cuando trabajas en una nueva característica para el proyecto.
    ```
        git checkout -b feature-new-search develop
        # aqui trabajamos los commits que sean necesarios, para q sea unida al main
        # hacemos merge desde develop a features 
        git merge --no-ff feature-new-search
        # borramos la rama feature y pusheamos al repo
        git branch -d feature-new-search
        git push origin develop
    ```

    ![feature](/imagenes/feature.png)
    
    > **Como funciona el `--no-ff`**

        el no ff hace que se cree un nuevo commit donde no se perderan los commits de la rama que esta siendo mergeada
        
    ![noff](/imagenes/ff.png)
    
    
    - Se crean desde: develop
    - Se fusionan en develop
    - Convención de nombre: feature-*

- **Release**: Cuando preparas el lanzamiento de una nueva versión.
    
    para la creacion y fusion de esta rama se debe seguir algo parecidoa a esto:
    
    ```
        ## 1. creamos la rama
        git checkout -b release-1.2.0 develop
        ## 2. hacemos un commit indicando la version
        git commit -am "Bumped version number to 1.2.0"
        ## 3. fusionar con develop y main con un tag
        git switch main
        git merge --no-ff release-1.2.0
        git tag -a 1.2.0

        git switch develop
        git merge --no-ff release-1.2.0

        ##probablemente haya conflictos con branch develop, lo solucionamos con un commit y luego borramos la rama release
        git branch -d release-1.2.0s
    ```
    - se crean de develop
    - se fucionan con develop y main
    - convension de nombre **release-**


- **Hotfix**: Para trabajar en cambios imprevistos como parches para arreglar un bug o un problema en producción. Traduciodo como parche o paño caliente
    para la creacion y fusion de esta rama se debe seguir algo parecido a a esto:
    ```
        #1. creacion de rama
        $ git switch -c hotfix-2.5.1 main

        #Hacer bump de la versión es opcional y depende
        ./bump-version.sh 2.5.1

        # Hacemos el commit con el arreglo del problema
        $ git commit -m "Fix bug causing app not working properly"

        # Fusionamos la rama hotfix con la rama main
        $ git switch main
        $ git merge --no-ff hotfix-2.5.1

        #tambien fusionar a la rama develop
        $ git switch develop
        $ git merge --no-ff hotfix-2.5.1

        # y eliminamos esta rama
        $ git branch -d hotfix-2.5.1
    ```
    > aveces que release ya este preparado, por lo q se deberia hacer el merge a release, xq luego esta hara merge con develop
    - se crea desde main
    - se fusiona con develop o release y main
    - convension de nombre: -<version>

#### Github FLow
Se basa en la creación de Pull Requests que serán discutidas para que se integren en la rama `main` que siempre está actualizada y lista para ser deployada
- muy usada en proyectos de codigo abierto
> que es pull request?
    >> abreviado PR, es una petición de cambios que se envía a través de una rama de GitHub. Lo que se pide es que los cambios que presenta la rama sean incorporados a otra rama (que normalmente es la rama principal pero no necesariamente tiene que ser siempre así).
- github flow maneja 2 tipos de ramas, la **main** y cualquier otra rama que se necesite.
- cuando se tiene que hacer el push de la rama auxiliar(por asi decirlo) al repo remoto se crea el PR, donde se indica la rama base, y la rama a fusionar, proporciona campos para el contexto y se crea el RP.

![github flow](/imagenes/giithub.png)

#### Trunk Based Development
 enfoque de desarrollo de software que se centra en mantener una única rama principal (trunk) como la fuente de verdad en el repositorio de código. 
 - A diferencia de otros modelos de ramificación más complejos, como GitFlow, que utilizan múltiples ramas para desarrollar y entregar características, TBD simplifica el proceso al fomentar el desarrollo directamente en la rama principal.

![tronco](/imagenes/tronco.png)

##### Funcionamiento
- todos los cambios se desarrollan y prueban directamente en la rama principal (trunk). Esto significa que los desarrolladores realizan sus cambios directamente sobre la rama principal y no se crean ramas separadas para cada función o corrección de errores.

- Sigue el siguiente flujo de trabajo:

![tronco](/imagenes/tronco2.png)

##### Algunas consideraciones
- Necesitas contar con un sistema de Integración Continua
- El equipo trabaja usando técnicas como la programación a pares o la programación en grupo
- Se deben hacer commits constantemente
- Existen redes de seguridad automatizadas que deshacen un pase a producción en el caso que algo haya salido mal.
- no hay“días de despliegue”
##### Algunos beneficios
- Integración continua y menos fricción
- Menos trabajo manual
- Despliegue a producción continuo


#### Ship, Show, Ask
combina la idea de crear Pull Request con la habilidad de seguir publicando cambios rápidamente.
Los cambios que creamos en el repositorio se categorizan en tres:
- Ship: Se fusiona en la rama principal sin revisión
- Show: Abre una petición de cambios para que sean revisados por CI pero se fusiona inmediatamente
- Ask: Abre una PR para discutir los cambios antes de fusionarlos

![SSA](/imagenes/ssa.png)

##### Ship
Ship significa que vamos a hacer un cambio directamente a la rama principal.
- El commit va directamente a producción, sin pasar por Pull Request

![Ship](/imagenes/ship.png)

##### Show
Se usa Pull Request pero no esperamos revisiones manuales del código. Es decir, esperamos que los tests automatizados, pruebas de cobertura y
validación de código sean exitosos pero no que otra persona revise el código.

![Show](/imagenes/show.png)

##### Ask
similar a Show pero aquí sí esperamos al feedback de nuestro equipo ante de fusionar la rama.
- La idea es que la rama dure el mínimo tiempo posible para no bloquear el trabajo de otros miembros del equipo
- Con Ask sí esperamos que el equipo revise la Pull Request. No esperamos aprobación, esperamos conversación para eliminar la incertidumbre.

![ask](/imagenes/ask.png)

##### reglas
- Tenemos un buen sistema de CI/CD
- Confiamos en el equipo y existen buenas prácticas de desarrollo.
- Las ramas son lo más pequeñas posibles
- El equipo ha sabido lidiar con el ego individual

#### Conclusiones sobre las estrategias de flujo de trabajo 
- Cada equipo, cada desarrollo, cada proyecto... son circunstancias diferentes que seguro, hay que lidiar de forma distinta.
- Adptar cualquiera de los flujo de trabajo que mejor se adapte
- No cambiar la metodologia de trabajo de un dia para otro.

### Clase 6 
### Alguna buenas practicas acerca de commits
 > **cada cuanto deberia hacer un commmit?**
 >>hacer commits pequeños con significado, dividir el trabajo en pequeñas partes
> **como escribir un buen commit**
- usar el verbo imperativo: (Add, Change, Fix, Remove).
    
    por ejemplo:
    - ...add a new search feature
    - ...fix a problem with the topbar
    - ...change the default system color
    - ...remove a random notification
- no usar punto final ni puntos suspensivos
- usar maximo 50 caracteres para el mensaje
- añiadir el texto necesario en el cuerpo del mensaje del commit
    - `git commit -m "Add summary of commit" -m "This is a message to add more context."` o `git commit`
- Usa un prefijo para tus commits para hacerlos más semánticos
![SSA](/imagenes/commit.png)
- algunos prefijos:
    - feat: para una nueva característica para el usuario.
    - fix: para un bug que afecta al usuario.
    - perf: para cambios que mejoran el rendimiento del sitio.
    - build: para cambios en el sistema de build, tareas de despliegue o instalación.
    - ci: para cambios en la integración continua.
    - docs: para cambios en la documentación.
    - refactor: para refactorización del código como cambios de nombre de variables
    o funciones.
    - style: para cambios de formato, tabulaciones, espacios o puntos y coma, etc; no
    afectan al usuario.
    - test: para tests o refactorización de uno ya existente.
- usar utilidades para hacer commit

### Algunas buenas practiacs acerca de ramas
- Sé consistente al nombrar tus ramas, dependiendo de como esté definido con el equipo
- Usa el nombre de la acción que se realiza en la rama
    por ejemplo:
    - bug: Cambios de código para arreglar un bug conocido.
    - feature: Desarrollo de una nueva característica.
    - experiment: Experimentos que nunca serán fusionados.
    - hotfix: Cambio rápido de un error crítico.
- puedes usar los IDs de JIRA o el sistema de tickets que uses
- no alterar el historial del proyecto(solo para casos especiales)
- No hacer commit de código generado ni configuración particular
### Algunas buenas practicas de pull request o PR
- Léete el archivo CONTRIBUTING.md o sigue el estilo del repositorio, en caso se quiera contribuir
- Respeta el estilo del repositorio
- Enfoca tu código en una sola cosa
- Es mucho más fácil revisar y aceptar una Pull Request que hace una sola cosa
- Explica tu Pull Request
- tener cuidado con el nombre del rama principal, puede ser main o master, ahora se usa main

## Clase 7
### Deshacer cambios
se lo hace cuando dejo de funcionar el proyecto, recuperar alguna parte del codigo
### Comandos destructivos
afectan el historial de commits
-  commit amend
- `git reset` -- soft o hard : retornar a un commit sin poder volver al futuro.
    - hard: descartar todos los commits q nos saltamos, borra todo 
    - soft: mantiene cambios antes de volver al pasado. igual borra todo 
- `git reset --soft HEAD~numero de commit al q quieres viajar`
### Comandos no destructivos
trabajan en base al historial sin afectarlo
- `git revert HEAD~numero de commit al q quieres viajar`
- tambien se puede traer archivos eliminados

- `git checkout idCommit`: volver al pasado, y extraer funciones o archivos. Es util cuando un commit agrupa varias cosas. 
- para traer archivos: `git checkout idCommit NOmbreArchivo.extension`
