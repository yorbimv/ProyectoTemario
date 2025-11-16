# 🔰 Módulo I: Fundamentos y Configuración Inicial

> **Objetivo:** Adquirir los cimientos teóricos de Git y GitHub, comprender su importancia en el desarrollo profesional y dominar la configuración inicial para empezar a trabajar con control de versiones.

---

## ➡️ Índice

- [**1. Fundamentos Teóricos**](#1-fundamentos-teóricos-git-y-github)
- [**2. Configuración e Inicialización**](#2-configuración-e-inicialización-práctica)
- [**3. Buenas Prácticas: Conventional Commits**](#3-buenas-prácticas-mensajes-de-commit)

---

<a id="1-fundamentos-teóricos-git-y-github"></a>

## 🚩 1. Fundamentos Teóricos: Git y GitHub

Esta sección cubre la base conceptual: qué es el control de versiones, la diferencia entre Git y GitHub, y por qué son imprescindibles en el ámbito de la programación.

### 1.1. Conceptos

#### 1.1.1. ¿Qué es Git?

**Git** es el **Sistema de Control de Versiones Distribuido (DVCS)** más popular del mundo. Es el **software** que instalas localmente en tu máquina.

- **Función Principal:** Actuar como una "máquina del tiempo" local, rastreando y registrando cada cambio en tu código.
- **Comando Clave:** Permite guardar puntos de restauración llamados _commits_.

#### 1.1.2. ¿Qué es GitHub?

**GitHub** es la **Plataforma de Alojamiento Web** que usa Git. Es un servicio en la nube donde almacenas tus repositorios remotos.

- **Función Principal:** Centralización, _backup_ de código y colaboración en equipo (_Pull Requests_).
- **Diferencia Fundamental:** **Git** es la herramienta (el motor); **GitHub** es el servicio (la nube social).

### 1.2. Importancia Profesional

El dominio de Git y GitHub es un **estándar de la industria** por:

- **Colaboración Segura:** Permite que equipos trabajen en el mismo proyecto sin sobrescribir el trabajo de otros.
- **Portafolio:** Tu perfil de GitHub sirve como tu currículum de código para empleadores.

---

<a id="2-configuración-e-inicialización-práctica"></a>

## ⚙️ 2. Configuración e Inicialización Práctica

Este apartado te guía paso a paso para la instalación, la configuración de tu identidad y la creación de tu primer repositorio local.

### 2.1. Instalación de Git

| Sistema Operativo | Enlace de Descarga / Método Detallado                                                                |
| :---------------- | :--------------------------------------------------------------------------------------------------- |
| **macOS**         | **Recomendado:** Usa **Homebrew** para obtener la versión más reciente: `brew install git`.          |
| **Windows**       | Descargar e instalar desde el instalador oficial de [git-scm.com](https://git-scm.com/download/win). |
| **Linux**         | Utiliza el gestor de paquetes (ej. Debian/Ubuntu): `sudo apt-get install git`.                       |

> ℹ️ **Verificación:** Una vez instalado, verifica la versión en tu Terminal: `git --version`.

### 2.2. Comandos Esenciales de Terminal

Antes de crear un proyecto, es vital saber cómo moverte en la Terminal (Mac/Linux) o Git Bash (Windows).

| Comando          | Propósito                                  | Ejemplo de Uso         |
| :--------------- | :----------------------------------------- | :--------------------- |
| `cd [carpeta]`   | Cambiar de directorio (navegar).           | `cd ~/Proyectos`       |
| `ls`             | Listar el contenido del directorio actual. |                        |
| `mkdir [nombre]` | Crear un nuevo directorio (carpeta).       | `mkdir mi-primer-repo` |

### 2.3. Inicialización del Proyecto

Sigue estos pasos para crear tu primer repositorio local (`hello-git`).

| Paso                    | Comando (Terminal) | Propósito y Explicación                                                                                   |
| :---------------------- | :----------------- | :-------------------------------------------------------------------------------------------------------- |
| **1. Crear Carpeta**    | `mkdir hello-git`  | Crea la carpeta del proyecto usando el comando de terminal.                                               |
| **2. Entrar a Carpeta** | `cd hello-git`     | Navega al directorio creado.                                                                              |
| **3. Inicializar Git**  | **`git init`**     | **¡Clave!** Crea la subcarpeta oculta `.git/` y convierte el directorio en un repositorio Git rastreable. |

> Opcional: Puedes abrir el proyecto en VS Code desde la Terminal con el comando `code .`

### 2.4. Configuración de Credenciales

Esta configuración es **global** y se aplica a todos tus proyectos. Es tu firma digital.

| Configuración | Comando                                         | Explicación                                                               |
| :------------ | :---------------------------------------------- | :------------------------------------------------------------------------ |
| **Nombre**    | `git config --global user.name "Tu Nombre"`     | Define el nombre que aparecerá como autor en todos tus commits.           |
| **Correo**    | `git config --global user.email "tu@email.com"` | Define el email asociado a tus commits (debe coincidir con el de GitHub). |

> 📌 **El Archivo `.gitconfig`:** Al usar `--global`, esta información se guarda permanentemente en el archivo `.gitconfig` en tu directorio principal (`~/`).

### 2.5. Creación de Atajos (Alias de Git)

Los **alias** son atajos personalizados que creas para comandos largos y frecuentes de Git, lo que acelera tu trabajo en la Terminal. Se guardan en el mismo archivo global de configuración (`.gitconfig`).

#### Cómo Crear un Alias

Se usa el comando `git config` en la sección `alias`:

Ejemplo:

> git config --global alias.[nombre_del_alias] "[comando_completo]"

| Alias      | Comando Completo        | Uso (`git [alias]`) | Propósito                                                        |
| :--------- | :---------------------- | :------------------ | :--------------------------------------------------------------- |
| **`st`**   | `status`                | `gs`                | Muestra el estado de los archivos (más rápido que `git status`). |
| **`co`**   | `checkout`              | `gck`               | Atajo para cambiar de ramas.                                     |
| **`ci`**   | `commit -m`             | `gc "mensaje"`      | Atajo para crear un _commit_ con mensaje.                        |
| **`br`**   | `branch`                | `gbr`               | Lista las ramas.                                                 |
| **`tree`** | `log --oneline --graph` | `git lo`            | Muestra el historial de _commits_ de forma compacta y visual.    |

Para visualizar los alias

> `git config --global --get-regexp alias`

<a id="3-buenas-prácticas-mensajes-de-commit"></a>

## 📖 3. Buenas Prácticas: Mensajes de Commit

Utilizamos el estándar **Conventional Commits** para mantener un historial limpio, profesional y legible.

| Tipo           | Propósito                                                        | Ejemplo Práctico                                               |
| :------------- | :--------------------------------------------------------------- | :------------------------------------------------------------- |
| **`feat`**     | **Nuevas Funcionalidades.** (Feature)                            | `feat: Agregada validación de input en formulario de registro` |
| **`fix`**      | **Corrección de Errores.** (Bug)                                 | `fix: Corregido error que causaba crash al cerrar sesión`      |
| **`docs`**     | **Documentación.** (READMEs, comentarios, guías)                 | `docs: Actualizada la tabla de comandos esenciales`            |
| **`style`**    | **Estilo/Formato.** (Presentación visual o formato de código)    | `style: Actualizada imagen de portada a formato horizontal`    |
| **`refactor`** | **Refactorización.** (Mejora de estructura sin cambio de lógica) | `refactor: Simplificada la lógica de la función de parseo`     |
| **`test`**     | **Pruebas.** (Añadir o corregir tests)                           | `test: Añadidos tests unitarios para la función de login`      |
| **`chore`**    | **Mantenimiento.** (Configuración, `.gitignore`, dependencias)   | `chore: Agregada regla .DS_Store al .gitignore`                |

---

### 3.1. Comando Bonus: Ignorar Archivos

Si has subido accidentalmente archivos de sistema como `.DS_Store`, usa este comando para borrarlos del historial:

```bash
git rm -r --cached .DS_Store
```
