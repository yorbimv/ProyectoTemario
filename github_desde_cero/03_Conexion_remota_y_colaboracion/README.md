# 🌐 Módulo III: Conexión Remota y Colaboración

> **Objetivo:** Aprender a conectar tu repositorio local con GitHub, sincronizar tu trabajo con el mundo exterior (`push`, `pull`) y entender los mecanismos de colaboración (`Pull Requests`).

---

## ➡️ Índice de Lecciones

- [**1. Repositorios Remotos (Origin)**](#1-repositorios-remotos-origin)
- [**2. Sincronización de Cambios (Push, Pull, Fetch)**](#2-sincronización-de-cambios-push-pull-fetch)
- [**3. El Flujo de Colaboración (Pull Requests)**](#3-el-flujo-de-colaboración-pull-requests)
- [**4. Resumen de Comandos**](#4-resumen-de-comandos)

---

<a id="1-repositorios-remotos-origin"></a>

## 🚩 1. Repositorios Remotos: El Origen

Un repositorio remoto es la copia de tu proyecto que se almacena en un servidor (GitHub). Es esencial para el _backup_ y la colaboración.

### 1.1. Creación en GitHub

Antes de la conexión, debes crear el repositorio en la plataforma web.

- **Paso clave:** Al crear, deja las casillas "Add a README file", ".gitignore" y "Choose a license" **DESMARCADAS**.

### 1.2. Conexión Local-Remota (`git remote`)

El comando `git remote` crea un vínculo entre tu repositorio local y la URL de GitHub.

> Por convención, el apodo para el repositorio principal es **`origin`**.

| Comando                       | Propósito                                                             | Ejemplo                                                      |
| :---------------------------- | :-------------------------------------------------------------------- | :----------------------------------------------------------- |
| `git remote add origin [URL]` | **Conexión Inicial.** Vincula el repositorio local con la URL remota. | `git remote add origin https://github.com/user/proyecto.git` |
| `git remote -v`               | **Verificación.** Muestra la URL configurada para `origin`.           | `git remote -v`                                              |

---

<a id="2-sincronización-de-cambios-push-pull-fetch"></a>

## ⚙️ 2. Sincronización de Cambios (`push`, `pull`, `fetch`)

Estos comandos son los mecanismos para intercambiar _commits_ entre tu máquina local y el servidor remoto.

### 2.1. Subir Cambios (`git push`)

Envía los _commits_ locales al repositorio remoto.

| Comando                     | Propósito                                                                                     | Ejemplo                   |
| :-------------------------- | :-------------------------------------------------------------------------------------------- | :------------------------ |
| `git push -u origin [rama]` | **(Primera vez)** Sube los _commits_ y establece la **relación de seguimiento** (`upstream`). | `git push -u origin main` |
| `git push`                  | Sube _commits_ a la rama remota, una vez que el seguimiento ha sido establecido.              | `git push`                |

> El argumento -u en el comando `git push -u origin main` significa --set-upstream. Su propósito es establecer una relación de seguimiento (tracking relationship) entre tu rama local y la rama remota.

### 2.1.1 🔑 Significado y Propósito de -u

Cuando ejecutas `git push -u origin main` por primera vez:Sube los commits: Envía los commits de tu rama local (main) al repositorio remoto (origin).

Establece Seguimiento (-u): Le dice a Git: "De ahora en adelante, asume que mi rama local main está directamente relacionada con la rama remota origin/main".

#### Beneficio Práctico

Gracias a la bandera -u, todas las veces posteriores que quieras subir o bajar cambios, no necesitarás especificar el nombre del remoto (origin) ni el nombre de la rama (main):

| Acción | Antes de -u            | Después de -u |
| :----- | :--------------------- | :------------ |
| Subir  | `git push origin main` | `git push`    |
| Bajar  | `git pull origin main` | `git pull`    |

En resumen, el -u es una configuración de única vez que hace que los comandos de sincronización sean mucho más cortos y eficientes en el futuro.

### 2.2. Descargar y Sincronizar

| Comando                      | Función Clave                                                                                                                         | Ejemplo                |
| :--------------------------- | :------------------------------------------------------------------------------------------------------------------------------------ | :--------------------- |
| **`git pull origin [rama]`** | **Descarga Y Fusiona.** Baja los _commits_ remotos y los integra automáticamente a tu rama local. Es un atajo para `fetch` + `merge`. | `git pull origin main` |
| **`git fetch origin`**       | **Solo Descarga.** Baja los _commits_ remotos a tu repo local, pero **NO** los aplica ni los fusiona a tu rama de trabajo.            | `git fetch origin`     |

> 💣 **Conflicto al hacer `pull`:** Si `git pull` detecta que tú y otro colaborador modificaron la misma línea de código, se detendrá y requerirá que resuelvas el conflicto manualmente (como se vio en el Módulo II).

---

<a id="3-el-flujo-de-colaboración-pull-requests"></a>

## 📖 3. El Flujo de Colaboración (Pull Requests)

El **Pull Request (PR)** es una **función de GitHub** esencial para el trabajo en equipo; permite proponer código y someterlo a revisión.

### 3.1. Proceso de PR

1.  **Trabajo:** Creas y terminas tu funcionalidad en una rama separada.
2.  **Sincronización:** Subes tu rama a GitHub (`git push origin mi-feature`).
3.  **PR:** Creas la solicitud en la interfaz web de GitHub para que tu rama se fusione en `main`.
4.  **Revisión:** Un compañero revisa tu código (_Code Review_).
5.  **Merge:** Una vez aprobado, el PR se fusiona en `main`.

### 3.2. Comandos Esenciales Post-Merge

Después de que el código se fusiona en GitHub, debes sincronizar tu copia local:

| Comando                | Propósito                                                   | Flujo de Sincronización               |
| :--------------------- | :---------------------------------------------------------- | :------------------------------------ |
| `git switch main`      | Te mueves a la rama principal.                              | Necesario antes de bajar los cambios. |
| `git pull origin main` | Bajas el código recién fusionado de GitHub.                 | Actualiza tu `main` local.            |
| `git branch -d [rama]` | Eliminas la rama local de trabajo que ya ha sido integrada. | Limpieza final.                       |

---

<a id="4-resumen-de-comandos"></a>

## 📝 4. Resumen de Comandos

| Comando                       | Descripción Breve                                        | Categoría      |
| :---------------------------- | :------------------------------------------------------- | :------------- |
| `git remote add origin [URL]` | Conecta el repo local al repositorio remoto.             | Configuración  |
| `git push -u origin main`     | Sube commits por primera vez y establece el seguimiento. | Sincronización |
| `git pull origin main`        | Descarga los cambios remotos y los fusiona.              | Sincronización |
| `git fetch`                   | Descarga los cambios remotos **sin fusionar**.           | Sincronización |
| `git push origin [rama]`      | Sube una rama para crear un Pull Request.                | Colaboración   |

---
