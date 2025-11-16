<a id="1-el-ciclo-de-vida-del-commit"></a>

## 🚩 1. El Ciclo de Vida del Commit (Lecciones 7-10)

El proceso de guardar cambios en Git se divide en tres estados. Comprender estos estados es fundamental para no perder información y para decidir qué cambios quieres incluir en tu punto de restauración (el _commit_).

### 1.1. Los Tres Estados de Git

| Estado                   | Descripción para el Novato                                                                                                                  | Comando Implicado          |
| :----------------------- | :------------------------------------------------------------------------------------------------------------------------------------------ | :------------------------- |
| **1. Working Directory** | Es tu escritorio. Los archivos han sido modificados, pero Git aún no les está prestando atención.                                           | _Modificación de archivos_ |
| **2. Staging Area**      | El "**Área de Preparación**". Es como una cesta de compras. Seleccionas **exactamente** qué cambios quieres guardar en el próximo _commit_. | `git add`                  |
| **3. Repository**        | El historial permanente. El cambio ya está guardado como un punto de restauración seguro y numerado.                                        | `git commit`               |

> **Analogía:** Modificas el archivo (Working), lo pones en la canasta de _staging_ (`git add`), y luego pagas en caja (`git commit`) para que quede registrado en el historial del banco (Repository).

### 1.2. El Flujo de Trabajo Básico (El Ciclo ADD $\rightarrow$ COMMIT)

Este es el ciclo que debes repetir cada vez que terminas una tarea o un cambio significativo en tu código:

#### 1.2.1. Revisar el Estado (`git status`) - L7

Antes de guardar, siempre debes saber dónde estás. `git status` es tu GPS.

| Comando      | Propósito                                                                                          | Salidas Comunes                                                                                                                   |
| :----------- | :------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| `git status` | Muestra el estado actual del repositorio, qué archivos han sido modificados y dónde se encuentran. | **Rojo:** Archivo modificado pero no en Staging (Working Directory). <br> **Verde:** Archivo listo para el commit (Staging Area). |

#### 1.2.2. Preparar los Cambios (`git add`) - L8

Mueve los archivos modificados desde el **Working Directory (Rojo)** hacia el **Staging Area (Verde)**.

| Comando             | Propósito                                                                                 | Explicación          |
| :------------------ | :---------------------------------------------------------------------------------------- | :------------------- |
| `git add [archivo]` | Añade un archivo específico al _staging_.                                                 | `git add index.html` |
| `git add .`         | Añade **todos** los archivos nuevos y modificados al _staging_. **(Usar con precaución)** |                      |

> ⚠️ **Práctica Recomendada:** Evita usar `git add .` si has hecho muchos cambios. Es mejor añadir los archivos uno por uno para asegurar que solo guardas cambios relacionados con una única tarea.

#### 1.2.3. Guardar el Punto de Restauración (`git commit`) - L9

Este comando toma los cambios que están en el **Staging Area** y los guarda **permanentemente** en el historial del repositorio.

| Comando                     | Propósito                                        | Explicación                                            |
| :-------------------------- | :----------------------------------------------- | :----------------------------------------------------- |
| `git commit -m "[mensaje]"` | Crea un _commit_ con un mensaje corto y conciso. | `git commit -m "feat: Agregada seccion de bienvenida"` |

> 💡 **Nota:** El mensaje debe seguir la convención de `feat:`, `fix:`, `docs:`, etc. (Visto en el Módulo I).

#### 1.2.4. Revisar el Historial (`git log`) - L10

Permite ver la lista completa de todos los _commits_ que se han hecho en tu proyecto.

| Comando   | Propósito                                   | Salida Clave                                                           |
| :-------- | :------------------------------------------ | :--------------------------------------------------------------------- |
| `git log` | Muestra el historial completo de _commits_. | **HASH (ID):** Un código único (ej. `a1b2c3d4...`) para cada _commit_. |

---

## 📝 1.3. Comandos Esenciales (Ciclo Básico)

| Comando               | Descripción Breve                                   | Categoría    |
| :-------------------- | :-------------------------------------------------- | :----------- |
| `git status`          | Verifica los archivos modificados (rojos o verdes). | Flujo Básico |
| `git add .`           | Añade todos los cambios al _Staging Area_.          | Flujo Básico |
| `git commit -m "..."` | Guarda el punto de restauración en el repositorio.  | Flujo Básico |
| `git log`             | Muestra el historial completo de _commits_.         | Historial    |

<a id="2-gestión-de-ramas-branching"></a>

## ⚙️ 2. Gestión de Ramas (Branching) (Lecciones 11-15)

Las ramas (o _branches_) son el corazón de la colaboración y el desarrollo seguro en Git. Piensa en una rama como una **línea de tiempo de desarrollo independiente**. Permite a los desarrolladores trabajar en nuevas características o corregir errores sin romper la versión principal del código.

### 2.1. El Concepto de Ramas

- **Ramas vs. Carpetas:** Una rama no es una carpeta, es solo una etiqueta que apunta a un _commit_ específico en el historial. Permite que el mismo código exista en múltiples versiones a la vez.
- **Rama `main` (Principal):** Es la rama por defecto. Contiene la versión **estable y funcional** del proyecto. **Nunca se trabaja directamente en `main`**; siempre se crea una nueva rama a partir de ella.
- **HEAD:** Es un puntero que indica en qué rama estás trabajando actualmente.

### 2.2. Flujo de Comandos Esenciales

Para trabajar con ramas, debes dominar tres comandos principales:

#### 2.2.1. Crear y Listar Ramas (`git branch`) - L11

| Comando               | Propósito                                                                                | Explicación                |
| :-------------------- | :--------------------------------------------------------------------------------------- | :------------------------- |
| `git branch`          | Lista todas las ramas en tu repositorio. La rama activa se marca con un asterisco (`*`). |                            |
| `git branch [nombre]` | Crea una nueva rama partiendo del _commit_ donde estás actualmente.                      | `git branch nueva-feature` |

#### 2.2.2. Cambiar de Rama (`git checkout` o `git switch`) - L12

Para empezar a trabajar en la nueva línea de tiempo, debes cambiarte a esa rama.

| Comando                  | Propósito                                                                       | Explicación                   |
| :----------------------- | :------------------------------------------------------------------------------ | :---------------------------- |
| `git switch [nombre]`    | **(Recomendado, moderna)** Cambia a la rama especificada.                       | `git switch nueva-feature`    |
| `git switch -c [nombre]` | **Crea y Cambia:** Crea la nueva rama e inmediatamente te mueve a ella (atajo). | `git switch -c fix-bug-login` |
| `git checkout [nombre]`  | **(Clásica)** Hace lo mismo que `git switch`.                                   | `git checkout nueva-feature`  |

#### 2.2.3. Combinar Cambios (`git merge`) - L13 y L14

Cuando terminas el trabajo en una rama (ej. `nueva-feature`), debes traer esos cambios a la rama principal (`main`).

| Comando                     | Proceso                   | Explicación                                                                         |
| :-------------------------- | :------------------------ | :---------------------------------------------------------------------------------- |
| **1. Ir a la Rama Destino** | `git switch main`         | Siempre debes estar en la rama que recibirá los cambios.                            |
| **2. Fusionar**             | `git merge [rama_origen]` | `git merge nueva-feature`. Esto combina el historial de `nueva-feature` con `main`. |

> 💣 **Conflictos (L14):** Si dos ramas modifican la misma línea de código, Git no sabe cuál mantener. Esto detiene el `merge` y requiere que edites manualmente el archivo para elegir el código correcto.

#### 2.2.4. Eliminar Ramas Terminadas (`git branch -d`) - L15

Una vez que el trabajo ha sido fusionado, la rama ya no es necesaria.

| Comando                  | Propósito                                                                                  | Explicación                    |
| :----------------------- | :----------------------------------------------------------------------------------------- | :----------------------------- |
| `git branch -d [nombre]` | Elimina la rama local **si ya ha sido fusionada** con éxito.                               | `git branch -d nueva-feature`  |
| `git branch -D [nombre]` | **(Force Delete)** Elimina la rama, incluso si no ha sido fusionada (usar con precaución). | `git branch -D rama-de-prueba` |

---

## 📝 2.3. Comandos Esenciales (Ramas)

| Comando                  | Descripción Breve                                       |
| :----------------------- | :------------------------------------------------------ |
| `git branch`             | Lista todas las ramas locales.                          |
| `git branch [nombre]`    | Crea una nueva rama.                                    |
| `git switch [nombre]`    | Cambia a la rama especificada.                          |
| `git switch -c [nombre]` | Crea y cambia a la nueva rama.                          |
| `git merge [rama]`       | Combina los cambios de la rama origen a la rama actual. |
| `git branch -d [nombre]` | Elimina una rama local fusionada.                       |

---

<a id="3-manipulación-del-historial"></a>

## 📖 3. Manipulación del Historial (Lecciones 16-18)

Deshacer o modificar el historial es común, pero requiere precaución. Git ofrece herramientas para "viajar en el tiempo", pero debes distinguir las opciones seguras (para código que ya está en GitHub) de las peligrosas (para código solo en tu máquina local).

### 3.1. Limpieza de Archivos No Rastreados (`git clean`) - L18

Este comando se usa para eliminar archivos que están en tu **Working Directory** pero que Git no está rastreando (archivos temporales, compilados, etc.).

| Comando         | Propósito                                                                                                                 | Explicación |
| :-------------- | :------------------------------------------------------------------------------------------------------------------------ | :---------- |
| `git clean -n`  | **(Safe Mode)** Muestra una vista previa de los archivos que serían eliminados. **Siempre** ejecuta este comando primero. |             |
| `git clean -f`  | **(Forzado)** Elimina todos los archivos no rastreados.                                                                   |             |
| `git clean -df` | Elimina archivos no rastreados **y directorios (carpetas)** no rastreados.                                                |             |

> ⚠️ **Advertencia:** `git clean` elimina archivos permanentemente, sin pasarlos a la papelera. Úsalo con mucho cuidado.

### 3.2. Deshacer el Historial de Forma Segura (`git revert`) - L17

Este es el método **seguro** y recomendado para deshacer _commits_ que **ya han sido subidos a GitHub** y están siendo usados por otros colaboradores.

- **Función:** Crea un **nuevo _commit_** cuyo único propósito es revertir (deshacer) los cambios introducidos por un _commit_ anterior.
- **Ventaja:** Preserva el historial original. No borra nada, sino que añade un _commit_ que anula el anterior.

| Comando                | Propósito                                                                                  | Explicación           |
| :--------------------- | :----------------------------------------------------------------------------------------- | :-------------------- |
| `git revert [HASH/ID]` | Crea un nuevo _commit_ que deshace los cambios del _commit_ especificado (usando su HASH). | `git revert a1b2c3d4` |

### 3.3. Deshacer el Historial Localmente (`git reset`) - L16

Este comando es más poderoso y **peligroso**, ya que reescribe la historia. Solo debe usarse para deshacer _commits_ que **solo existen en tu máquina local** y aún no han sido subidos a GitHub.

| Comando                    | Propósito                                                                                                      | Explicación                                          |
| :------------------------- | :------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------- |
| `git reset --soft [HASH]`  | Deshace el _commit_ **PERO** mantiene los cambios en el Staging Area (los deja listos para un nuevo _commit_). | El código permanece intacto.                         |
| `git reset --mixed [HASH]` | Deshace el _commit_ **Y** los saca del Staging Area, enviándolos al Working Directory (quedan en rojo).        | Opción por defecto, limpia el Staging.               |
| `git reset --hard [HASH]`  | **¡Peligroso!** Deshace el _commit_ **Y** elimina los cambios del Working Directory.                           | Borra permanentemente tu trabajo desde ese _commit_. |

### 3.4 Limpieza de Archivos No Rastreados (`git clean`) - L18

Este comando elimina archivos que están en tu **Working Directory** pero que Git no está rastreando (archivos temporales, compilados, etc.).

| Comando        | Propósito                                                                                                          | Nota de Seguridad                         |
| :------------- | :----------------------------------------------------------------------------------------------------------------- | :---------------------------------------- |
| `git clean -n` | **(Safe Mode)** Muestra una vista previa de los archivos que serían eliminados. **¡Siempre ejecuta esto primero!** |                                           |
| `git clean -f` | **(Forzado)** Elimina todos los archivos no rastreados del directorio.                                             | Borra archivos sin pasar por la papelera. |

> 🔑 **Clave:** En todos los casos, el `HASH/ID` es el identificador del _commit_ al que quieres **volver**.

---

<a id="4-comandos-esenciales-módulo-ii"></a>

## 📝 4. Comandos Esenciales (Módulo II)

Esta tabla consolida todos los comandos vistos en el Módulo II (Flujo Básico, Ramas y Manipulación).

| Comando                   | Descripción Breve                                                         | Categoría    |
| :------------------------ | :------------------------------------------------------------------------ | :----------- |
| `git status`              | Muestra el estado actual del Working Directory y Staging Area.            | Flujo Básico |
| `git add .`               | Prepara todos los cambios para el siguiente commit.                       | Flujo Básico |
| `git commit -m "..."`     | Guarda los cambios preparados permanentemente en el historial.            | Flujo Básico |
| `git log`                 | Muestra el historial completo de commits (para obtener el HASH).          | Historial    |
| `git switch -c [nombre]`  | Crea y cambia inmediatamente a una nueva rama.                            | Ramas        |
| `git merge [rama]`        | Combina el historial de una rama a la rama actual.                        | Ramas        |
| `git revert [HASH]`       | **Seguro:** Deshace un commit anterior creando un nuevo commit.           | Manipulación |
| `git reset --hard [HASH]` | **Peligroso:** Elimina permanentemente los commits y los cambios locales. | Manipulación |

## 🚀 Próximo Paso: Módulo III

Con el Módulo II concluido, has dominado el flujo de trabajo esencial (`add/commit/branch/merge`) y la manipulación del historial.

El **Módulo III** se centrará en la **Conexión Remota**, es decir, cómo subir (`git push`) y bajar (`git pull` / `git fetch`) tu trabajo a GitHub, el trabajo con repositorios remotos y la creación de _Pull Requests_.
