# ✨ Módulo IV: Temas Avanzados y Herramientas Esenciales

> **Objetivo:** Dominar técnicas avanzadas como `rebase` para mantener un historial limpio, usar `stash` para gestionar cambios temporales y emplear _tags_ para marcar versiones estables del proyecto.

---

## ➡️ Índice de Lecciones (Navegación Rápida)

- [**1. La Fusión Limpia: Git Rebase**](#1-la-fusión-limpia-git-rebase)
- [**2. Gestión de Cambios Temporales: Git Stash**](#2-gestión-de-cambios-temporales-git-stash)
- [**3. Marcado de Versiones: Git Tags**](#3-marcado-de-versiones-git-tags)
- [**4. Comandos Esenciales del Módulo**](#4-comandos-esenciales-módulo-iv)

---

<a id="1-la-fusión-limpia-git-rebase"></a>

## 🚩 1. La Fusión Limpia: Git Rebase (Lecciones 28-30)

El `rebase` es una alternativa poderosa al `merge` para integrar cambios. En lugar de crear un _commit_ de fusión, el `rebase` reescribe el historial, moviendo los _commits_ de tu rama al final de otra rama, resultando en un historial lineal y limpio.

- `git rebase [rama]` - Mover _commits_.
- `rebase` interactivo para reescribir y combinar _commits_ (`squashing`).
- **Advertencia:** Riesgos y cuándo NO usar `rebase` (nunca en _commits_ públicos).

---

<a id="2-gestión-de-cambios-temporales-git-stash"></a>

## ⚙️ 2. Gestión de Cambios Temporales: Git Stash (Lecciones 31-33)

El `stash` es una herramienta para guardar tu trabajo actual (cambios en _Working Directory_ y _Staging Area_) temporalmente sin necesidad de crear un _commit_. Es perfecto para cambiar rápidamente de ramas sin perder el progreso.

- `git stash` - Guardar cambios.
- `git stash pop` vs `git stash apply` - Recuperar cambios.
- Gestión de múltiples _stashes_.

---

<a id="3-marcado-de-versiones-git-tags"></a>

## 📖 3. Marcado de Versiones: Git Tags (Lecciones 34-35)

Los _tags_ son marcadores permanentes en el historial que se usan para identificar versiones importantes, como lanzamientos de software (v1.0.0, v2.1-beta, etc.).

- Creación de _tags_ ligeros y _tags_ anotados.
- `git push --tags` - Subir _tags_ al repositorio remoto.

---

<a id="4-comandos-esenciales-módulo-iv"></a>

## 📝 4. Comandos Esenciales (Módulo IV)

| Comando                  | Descripción Breve                                            | Categoría       |
| :----------------------- | :----------------------------------------------------------- | :-------------- |
| `git rebase [rama]`      | Mueve tu rama base al final de otra rama (historial lineal). | Rebase          |
| `git rebase -i [commit]` | Permite editar, reordenar o fusionar _commits_ antiguos.     | Rebase Avanzado |
| `git stash`              | Guarda temporalmente los cambios sin hacer commit.           | Stash           |
| `git stash pop`          | Restaura el último stash guardado y lo elimina de la lista.  | Stash           |
| `git tag -a [nombre]`    | Crea un _tag_ anotado para marcar una versión (ej. v1.0.0).  | Tags            |
| `git push --tags`        | Sube todos los tags locales al repositorio remoto.           | Tags            |

---

<a id="1-la-fusión-limpia-git-rebase"></a>

## 🚩 1. La Fusión Limpia: Git Rebase (Lecciones 28-30)

`git rebase` es una herramienta avanzada para reescribir el historial de _commits_. Su propósito es integrar cambios de una rama a otra, **evitando los _commits_ de fusión** que genera `git merge`.

### 1.1. Merge vs. Rebase

| Característica   | `git merge`                                         | `git rebase`                                             |
| :--------------- | :-------------------------------------------------- | :------------------------------------------------------- |
| **Historial**    | Mantiene la estructura de ramificación (no lineal). | Crea un historial **lineal** y limpio.                   |
| **Cómo Integra** | Crea un _commit_ adicional (`Merge Commit`).        | Mueve los _commits_ de la rama al final de la rama base. |
| **Seguridad**    | Muy seguro (no reescribe la historia).              | **Peligroso** (reescribe la historia).                   |

#### 1.1.1. Concepto Visual

Imagina que estás en la rama `feature-A` y quieres integrar los últimos cambios de `main`.

- **Con `merge`:** Creas un nodo de fusión que une ambas historias.
- **Con `rebase`:** Toma tus _commits_ de `feature-A` y los **reaplica** (uno por uno) como si hubieras empezado a trabajar desde el último _commit_ de `main`.

### 1.2. Flujo de Trabajo Básico de `rebase` (L28)

El uso más común es para "limpiar" tu rama antes de fusionarla con `main`.

1.  **Asegúrate de estar en tu rama de trabajo:**
    ```bash
    git switch feature-A
    ```
2.  **Ejecuta el rebase:**
    ```bash
    # Mueve todos los commits de feature-A para que parezca que fueron hechos DÉSPUES del último commit de main.
    git rebase main
    ```
3.  **Resultado:** Tu rama `feature-A` ahora está "limpia" y lista para un `merge` rápido (Fast-Forward) en `main` sin _merge commits_.

### 1.3. Rebase Interactivo (`git rebase -i`) (L29)

El _rebase_ interactivo es la herramienta más poderosa para la limpieza. Te permite **editar _commits_ antiguos** antes de que se reapliquen.

| Comando                | Propósito                                                    |
| :--------------------- | :----------------------------------------------------------- |
| `git rebase -i HEAD~N` | Inicia el modo interactivo para los últimos **N** _commits_. |

Al ejecutarlo, se abre un editor de texto con una lista de tus últimos _commits_ y opciones para cada uno:

| Opción       | Significado                                          | Uso Común                                                                                                                   |
| :----------- | :--------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------- |
| **`pick`**   | Usar el _commit_ tal cual.                           | Por defecto.                                                                                                                |
| **`squash`** | **Combinar** este _commit_ con el _commit_ anterior. | Útil para convertir 5 _commits_ pequeños (`fix: error`, `fix: error 2`) en un solo _commit_ limpio (`feat: nueva función`). |
| **`reword`** | Cambiar solo el mensaje del _commit_.                | Para corregir errores tipográficos en el mensaje.                                                                           |
| **`drop`**   | Eliminar completamente el _commit_.                  | Para borrar un _commit_ que no es necesario.                                                                                |

### 1.4. Advertencia: Cuándo NO Usar Rebase (L30)

El `rebase` reescribe la historia del proyecto. Los _commits_ antiguos obtienen **nuevos HASHes**.

> 🛑 **Regla de Oro:** **NUNCA** uses `git rebase` en _commits_ que ya han sido **subidos** (pushed) a un repositorio público o compartido (GitHub, GitLab, etc.).

- **Razón:** Si reescribes la historia de una rama compartida, cuando otro colaborador intente hacer un `pull`, Git verá dos historias diferentes para el mismo punto, lo que generará grandes conflictos y problemas de sincronización.

---

<a id="2-gestión-de-cambios-temporales-git-stash"></a>

## ⚙️ 2. Gestión de Cambios Temporales: Git Stash (Lecciones 31-33)

El `git stash` es una herramienta para guardar tu trabajo actual de forma temporal sin la necesidad de crear un _commit_. Es perfecto cuando necesitas cambiar rápidamente de rama para corregir un error urgente, pero no quieres hacer _commit_ de un trabajo incompleto.

> **Analogía:** Piensa en `git stash` como un "cajón" o un "estante" donde guardas todos tus cambios a medio hacer para que tu escritorio (el _Working Directory_) quede limpio instantáneamente.

### 2.1. Guardar y Listar Cambios (`git stash`) - L31

| Comando                    | Propósito                                                                                                  | Explicación                       |
| :------------------------- | :--------------------------------------------------------------------------------------------------------- | :-------------------------------- |
| `git stash save "mensaje"` | Guarda los cambios del _Working Directory_ y el _Staging Area_ en una pila temporal y limpia tu rama.      | `git stash save "Bugfix urgente"` |
| `git stash`                | Versión abreviada de `git stash save`.                                                                     |                                   |
| `git stash list`           | Muestra todos los _stashes_ que tienes guardados. Cada uno tiene un índice (ej. `stash@{0}`, `stash@{1}`). |                                   |

### 2.2. Recuperar Cambios (`git stash pop` vs `git stash apply`) - L32

Una vez que has resuelto el problema urgente en otra rama, vuelves a tu rama original y recuperas tu trabajo.

| Comando                   | Propósito                                                                                        | Consecuencia                                                            |
| :------------------------ | :----------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------- |
| `git stash pop`           | Restaura el **último _stash_ guardado** (`stash@{0}`) y lo **elimina** de la pila de _stashes_.  | **Recomendado** si sabes que ya terminaste con ese conjunto de cambios. |
| `git stash apply`         | Restaura un _stash_ específico (ej. `stash@{1}`), **pero lo mantiene** en la lista de _stashes_. | Útil si necesitas aplicar el mismo conjunto de cambios en varias ramas. |
| `git stash drop [indice]` | Elimina un _stash_ específico de la lista.                                                       | `git stash drop stash@{1}`                                              |

### 2.3. Limpieza de Stash (L33)

Si tienes muchos _stashes_ viejos que ya no necesitas:

| Comando           | Propósito                                   |
| :---------------- | :------------------------------------------ |
| `git stash clear` | Elimina **todos** los _stashes_ de tu pila. |

---

<a id="3-marcado-de-versiones-git-tags"></a>

## 📖 3. Marcado de Versiones: Git Tags (Lecciones 34-35)

Los **Tags** (etiquetas) son marcadores fijos que se colocan en un _commit_ específico de tu historial para señalar un punto importante, como un lanzamiento de software (ej. `v1.0.0`, `v2.5-beta`).

> **Diferencia con Ramas:** Una rama se mueve con cada nuevo _commit_; un _tag_ permanece **fijo** en el _commit_ donde fue creado.

### 3.1. Tipos de Tags

Git maneja dos tipos de _tags_:

| Tipo                     | Propósito                                                                      | Uso                                          | Nota                                         |
| :----------------------- | :----------------------------------------------------------------------------- | :------------------------------------------- | :------------------------------------------- |
| **Ligero (Lightweight)** | Solo una etiqueta que apunta a un _commit_.                                    | Uso rápido y local.                          | No incluye información del autor ni fecha.   |
| **Anotado (Annotated)**  | Un objeto completo que incluye el nombre del _tagger_, la fecha, y un mensaje. | **Recomendado** para lanzamientos oficiales. | Se verifica mejor y se considera permanente. |

### 3.2. Comandos para Crear Tags (L34)

Puedes crear un _tag_ en el _commit_ actual o en uno anterior (usando su HASH).

| Comando                              | Propósito                                         | Explicación                                    |
| :----------------------------------- | :------------------------------------------------ | :--------------------------------------------- |
| `git tag [nombre]`                   | Crea un **Tag Ligero** en el _commit_ actual.     | `git tag v1.0.0`                               |
| `git tag -a [nombre] -m "[mensaje]"` | Crea un **Tag Anotado** (profesional).            | `git tag -a v2.0 -m "Lanzamiento oficial 2.0"` |
| `git tag`                            | Lista todos los _tags_ creados en el repositorio. |                                                |

### 3.3. Compartir Tags Remotamente (L35)

Los _tags_, al igual que las ramas, deben subirse explícitamente a GitHub. Un `git push` normal **NO** sube los _tags_.

| Comando                      | Propósito                                                     | Explicación                                           |
| :--------------------------- | :------------------------------------------------------------ | :---------------------------------------------------- |
| `git push origin [tag_name]` | Sube un _tag_ específico al repositorio remoto.               | `git push origin v2.0`                                |
| `git push --tags`            | Sube **todos** los _tags_ que no se hayan subido previamente. | **Recomendado** después de una serie de lanzamientos. |

---

<a id="4-comandos-esenciales-módulo-iv"></a>

## 📝 4. Comandos Esenciales (Módulo IV)

Esta tabla consolida todos los comandos avanzados vistos en el Módulo IV.

| Comando                        | Descripción Breve                                               | Categoría       |
| :----------------------------- | :-------------------------------------------------------------- | :-------------- |
| `git rebase [rama]`            | Mueve tu rama base al final de otra rama (historial lineal).    | Rebase          |
| `git rebase -i HEAD~N`         | Permite editar, reordenar o fusionar los últimos N _commits_.   | Rebase Avanzado |
| `git stash save "mensaje"`     | Guarda temporalmente los cambios sin hacer _commit_.            | Stash           |
| `git stash pop`                | Restaura el último stash guardado y lo elimina de la lista.     | Stash           |
| `git tag -a [nombre] -m "..."` | Crea un _tag_ **anotado** para marcar una versión (ej. v1.0.0). | Tags            |
| `git push --tags`              | Sube todos los _tags_ locales al repositorio remoto.            | Tags            |

---

## ✅ Módulos de Git Completos

¡Felicidades! Con esto, has completado el contenido de los cuatro módulos del curso de Git y GitHub:

1.  **Fundamentos**
2.  **Flujo Esencial**
3.  **Conexión Remota**
4.  **Temas Avanzados**
