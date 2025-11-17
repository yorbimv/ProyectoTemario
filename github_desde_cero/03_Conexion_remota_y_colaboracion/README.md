# 🌐 Módulo III: Conexión Remota y Colaboración

> **Objetivo:** Aprender a conectar tu repositorio local con GitHub, sincronizar tu trabajo con el mundo exterior (`push`, `pull`) y entender los mecanismos de colaboración (`Pull Requests`).

---

## ➡️ Índice de Lecciones (Navegación Rápida)

- [**1. Repositorios Remotos**](#1-repositorios-remotos-el-origen)
- [**2. Sincronización de Cambios**](#2-sincronización-de-cambios-push-pull)
- [**3. El Flujo de Colaboración**](#3-el-flujo-de-colaboración-pull-requests)
- [**4. Comandos Esenciales del Módulo**](#4-comandos-esenciales-módulo-iii)

---

<a id="1-repositorios-remotos-el-origen"></a>

## 🚩 1. Repositorios Remotos: El Origen (Lecciones 19-20)

Esta sección cubre la creación del repositorio en GitHub y la conexión inicial con tu trabajo local.

### 1.1. Creación en GitHub (L19)

Pasos clave para iniciar un repositorio en la plataforma GitHub.

### 1.2. Conexión Local-Remota (L20)

El vínculo entre tu carpeta local (`.git/`) y el servidor en GitHub.

- `git remote add [nombre] [url]` - Añadir el enlace remoto (usualmente llamado `origin`).

---

<a id="2-sincronización-de-cambios-push-pull"></a>

## ⚙️ 2. Sincronización de Cambios (`push`, `pull`) (Lecciones 21-24)

Aquí se aprende a subir tu trabajo a GitHub y a mantenerte actualizado con los cambios de otros colaboradores.

- `git push` - Subir _commits_ al repositorio remoto.
- `git pull` - Descargar y fusionar los cambios del remoto.
- `git fetch` - Descargar cambios sin fusionarlos.
- Resolución de conflictos al hacer `pull`.

---

<a id="3-el-flujo-de-colaboración-pull-requests"></a>

## 📖 3. El Flujo de Colaboración (Pull Requests) (Lecciones 25-27)

El mecanismo estándar para proponer, revisar e integrar código en equipos.

- Concepto de _Pull Request_ (PR) y por qué se usa.
- Creación y gestión de una PR.
- Revisión de código (_Code Review_) y merge.

---

<a id="4-comandos-esenciales-módulo-iii"></a>

## 📝 4. Comandos Esenciales (Módulo III)

| Comando                       | Descripción Breve                                                       | Categoría      |
| :---------------------------- | :---------------------------------------------------------------------- | :------------- |
| `git remote add origin [URL]` | Conecta el repo local al repositorio remoto en GitHub.                  | Configuración  |
| `git push -u origin main`     | Sube los commits locales a la rama remota, configurando el seguimiento. | Sincronización |
| `git pull origin main`        | Descarga los cambios remotos y los fusiona en la rama local actual.     | Sincronización |
| `git fetch`                   | Descarga los cambios remotos (solo copia) sin fusionarlos.              | Sincronización |

---

<a id="1-repositorios-remotos-el-origen"></a>

## 🚩 1. Repositorios Remotos: El Origen (Lecciones 19-20)

Un repositorio remoto es la copia de tu proyecto que se almacena en un servidor en internet (como GitHub). Es esencial para el _backup_, la colaboración y el despliegue de tu código.

### 1.1. Creación del Repositorio en GitHub (L19)

Antes de conectar tu proyecto local, debes crear el "destino" en la plataforma web de GitHub.

#### Pasos Clave:

1.  **Iniciar Sesión:** Accede a tu cuenta de GitHub.
2.  **Crear Nuevo:** Haz clic en el botón **`New`** (Nuevo) o en el signo de **`+`**.
3.  **Nombrar:** Asigna un nombre al repositorio (debe coincidir con tu proyecto local, aunque no es obligatorio).
4.  **Configuración:**
    - Selecciona **`Public`** (público) o **`Private`** (privado).
    - **Importante:** Deja las casillas "Add a README file", ".gitignore" y "Choose a license" **DESMARCADAS**. Esto es crucial porque ya tienes archivos localmente y Git necesita que el repositorio remoto esté vacío para la conexión inicial.
5.  **Finalizar:** Haz clic en **`Create repository`**.

Una vez creado, GitHub te mostrará una página con la URL de tu nuevo repositorio (ej. `https://github.com/tu-usuario/nombre-repo.git`).

### 1.2. Conexión Local-Remota (`git remote`) (L20)

El comando `git remote` se encarga de decirle a tu Git local dónde está el servidor de GitHub.

#### El Concepto de `origin`

Por convención, el primer y principal repositorio remoto de un proyecto siempre se llama **`origin`**. Es simplemente un apodo para la URL larga.

| Comando                       | Propósito                                                                                                                         | Explicación                                                 |
| :---------------------------- | :-------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------- |
| `git remote add origin [URL]` | **¡Conexión Inicial!** Vincula tu repositorio local con la URL de GitHub.                                                         | `git remote add origin https://github.com/user/project.git` |
| `git remote -v`               | **Verificación:** Muestra la lista de remotos que tienes configurados, incluyendo su URL de _fetch_ (descarga) y _push_ (subida). |                                                             |

#### Ejemplo de Flujo Inicial

Si estás en la carpeta de tu proyecto local (`hello-git`):

1.  **Añade el enlace remoto (URL que te dio GitHub):**
    ```bash
    git remote add origin [https://github.com/tu-usuario/mi-proyecto.git](https://github.com/tu-usuario/mi-proyecto.git)
    ```
2.  **Verifica la conexión:**
    ```bash
    git remote -v
    ```
    (Debería mostrar la URL de `origin` dos veces).

---

<a id="2-sincronización-de-cambios-push-pull"></a>

## ⚙️ 2. Sincronización de Cambios (`push`, `pull`, `fetch`) (Lecciones 21-24)

Una vez que tu repositorio local está conectado al remoto (`origin`), necesitas comandos para enviar y recibir _commits_.

### 2.1. Subir Cambios a GitHub (`git push`) - L21

`git push` es el comando que toma todos tus _commits_ locales y los envía al repositorio remoto.

| Comando                     | Propósito                                                                                  | Explicación               |
| :-------------------------- | :----------------------------------------------------------------------------------------- | :------------------------ |
| `git push origin [rama]`    | Sube tus commits de la rama local (ej. `main`) a la rama remota (`origin/main`).           | `git push origin main`    |
| `git push -u origin [rama]` | **(Primera vez)** Sube los commits y establece una **relación de seguimiento** (upstream). | `git push -u origin main` |

> 📌 **¿Qué es `-u`?** La bandera `-u` (o `--set-upstream`) solo se usa la primera vez. Después de esto, puedes simplemente escribir `git push` y Git sabrá que debe subir los commits a `origin/main`.

### 2.2. Descargar y Fusionar Cambios (`git pull`) - L22

`git pull` es el comando que usas cuando necesitas actualizar tu repositorio local con los _commits_ que otros colaboradores subieron a GitHub.

- **Función:** `git pull` es un atajo que ejecuta dos comandos en secuencia:
  1.  `git fetch`: Descarga los datos del remoto.
  2.  `git merge`: Fusiona esos datos descargados en tu rama local actual.

| Comando                  | Propósito                                                       |
| :----------------------- | :-------------------------------------------------------------- |
| `git pull origin [rama]` | Descarga y fusiona los cambios remotos en tu rama local actual. |

> 💣 **Conflictos al hacer `pull` (L23):** Si modificaste un archivo localmente y otro colaborador subió cambios a ese mismo archivo, `git pull` intentará fusionarlos y fallará. Debes resolver el conflicto manualmente (como aprendimos en el Módulo II) antes de que el `pull` pueda completarse.

### 2.3. Descargar Cambios sin Fusionar (`git fetch`) - L24

`git fetch` te permite inspeccionar los cambios remotos antes de aplicarlos a tu rama de trabajo local.

| Comando            | Propósito                                                                                         |
| :----------------- | :------------------------------------------------------------------------------------------------ |
| `git fetch origin` | Descarga los commits del remoto al repositorio local, pero **NO** los fusiona con tu rama actual. |

- **Uso:** Esto es útil para ver si hay nuevos _commits_ en GitHub sin riesgo de crear conflictos en tu trabajo actual.

### 2.4. Comandos Esenciales (Sincronización)

| Comando     | Descripción                                                               |
| :---------- | :------------------------------------------------------------------------ |
| `git push`  | Sube los commits locales al repositorio remoto.                           |
| `git pull`  | Descarga y fusiona los cambios del remoto (equivale a `fetch` + `merge`). |
| `git fetch` | Descarga los commits del remoto sin fusionarlos (solo inspección).        |

---

<a id="3-el-flujo-de-colaboración-pull-requests"></a>

## 📖 3. El Flujo de Colaboración (Pull Requests) (Lecciones 25-27)

Un **Pull Request (PR)** no es un comando de Git, sino una **función de GitHub** (la plataforma web). Es el mecanismo estándar de la industria para proponer que tus cambios sean revisados e integrados en la rama principal.

### 3.1. Concepto de Pull Request (PR) (L25)

El nombre "Pull Request" significa literalmente **"Solicitud de Extracción"**.

Cuando creas una PR, le estás diciendo al dueño del repositorio (o a la rama principal): "Tengo un código en mi rama que me gustaría que **jalaras** (`pull`) e integraras en tu rama".

- **¿Por qué se usa?** Permite que otros desarrolladores (**revisores**) vean, prueben y ofrezcan comentarios sobre tu código antes de que se fusione con la versión estable (`main`).

### 3.2. Creación y Flujo de una PR (L26)

El proceso sigue un flujo de trabajo muy definido:

1.  **Trabajo Aislado:** Creas una rama local (ej. `git switch -c mi-nueva-feature`).
2.  **Sincronización:** Subes la rama al remoto: `git push -u origin mi-nueva-feature`.
3.  **Creación de la PR:** Vas a GitHub, y la plataforma detectará tu nueva rama. Haces clic en **"Compare & pull request"**.
4.  **Revisión (Code Review):** Los revisores pueden dejar comentarios en líneas específicas de tu código.
5.  **Merge (Fusión):** Una vez que la PR es aprobada, el revisor (o tú) hace clic en **"Merge pull request"**. Esto ejecuta automáticamente un `git merge` en el servidor de GitHub, fusionando tu rama con `main`.

### 3.3. Comandos Esenciales Post-PR (L27)

Una vez que la PR se fusiona en GitHub, tu trabajo local debe reflejar esos cambios:

| Comando                | Propósito                                                 | Explicación                                                         |
| :--------------------- | :-------------------------------------------------------- | :------------------------------------------------------------------ |
| `git switch main`      | Te mueves a la rama principal.                            | Debes estar en `main` para recibir los cambios.                     |
| `git pull origin main` | Bajas los cambios recién fusionados de GitHub.            | Esto actualiza tu `main` local con el código que acabas de aprobar. |
| `git branch -d [rama]` | Eliminas tu rama de _feature_ local (ya no es necesaria). | Es buena práctica mantener limpio el repositorio local.             |

---

<a id="4-comandos-esenciales-módulo-iii"></a>

## 📝 4. Comandos Esenciales (Módulo III)

| Comando                       | Descripción Breve                                                       | Categoría      |
| :---------------------------- | :---------------------------------------------------------------------- | :------------- |
| `git remote add origin [URL]` | Conecta el repo local al repositorio remoto en GitHub.                  | Configuración  |
| `git push -u origin main`     | Sube los commits locales a la rama remota, configurando el seguimiento. | Sincronización |
| `git pull origin main`        | Descarga los cambios remotos y los fusiona en la rama local actual.     | Sincronización |
| `git fetch`                   | Descarga los cambios remotos (solo copia) sin fusionarlos.              | Sincronización |
| **`git push origin [rama]`**  | **Sube una rama al remoto para crear una PR.**                          | Colaboración   |

---

## ✅ Módulo III Concluido

¡Felicidades! Con esto, has completado los tres módulos esenciales para dominar Git y GitHub:

1.  **Módulo I:** Fundamentos y Configuración.
2.  **Módulo II:** Flujo de Trabajo (add/commit/branch/merge).
3.  **Módulo III:** Conexión Remota y Colaboración (`push`/`pull`/PRs).
