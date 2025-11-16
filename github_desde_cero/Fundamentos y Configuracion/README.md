# 🔰 Módulo I: Fundamentos y Configuración Inicial

> **Objetivo:** Adquirir los cimientos teóricos de Git y GitHub, comprender su importancia en el desarrollo profesional y dominar la configuración inicial para empezar a trabajar con control de versiones.

---

## ➡️ Índice de Lecciones

- [**Fundamentos Teóricos**](#1-fundamentos-teóricos-git-y-github)
- [**Configuración Práctica**](#2-configuración-inicial-práctica)
- [**Buenas Prácticas: Conventional Commits**](#3-buenas-prácticas-mensajes-de-commit)
- [**Comandos Esenciales del Módulo**](#4-comandos-básicos-de-git-módulo-i)

---

<a id="1-fundamentos-teóricos-git-y-github"></a>

## 🚩 1. Fundamentos Teóricos: Git y GitHub

Esta sección cubre la base conceptual: qué es el control de versiones, la diferencia entre Git y GitHub, y por qué son imprescindibles en el ámbito de la programación.

### 1.2. Conceptos

#### 1.2.1. ¿Qué es Git?

**Git** es el **Sistema de Control de Versiones Distribuido (DVCS)** más popular del mundo. Es el **software** que instalas localmente en tu máquina.

- **Función Principal:** Actuar como una "máquina del tiempo" local, rastreando y registrando cada cambio en tu código.
- **Comando Clave:** Permite guardar puntos de restauración llamados _commits_.

#### 1.2.2. ¿Qué es GitHub?

**GitHub** es la **Plataforma de Alojamiento Web** que usa Git. Es un servicio en la nube donde almacenas tus repositorios remotos.

- **Función Principal:** Centralización, _backup_ de código y colaboración en equipo (_Pull Requests_).
- **Diferencia Fundamental:** **Git** es la herramienta (el motor); **GitHub** es el servicio (la nube social).

### 1.3. Importancia Profesional

El dominio de Git y GitHub es un **estándar de la industria** por:

- **Colaboración Segura:** Permite que equipos trabajen en el mismo proyecto sin sobrescribir el trabajo de otros.
- **Portafolio:** Tu perfil de GitHub sirve como tu currículum de código para empleadores.

---

<a id="2-configuración-inicial-práctica"></a>

## ⚙️ 2. Configuración Inicial Práctica

Este apartado te guía paso a paso para instalar y configurar tu identidad, preparándote para crear tu primer repositorio.

### 2.1. Instalación de Git

| **Sistema Operativo** | **Enlace de Descarga / Método Detallado**                                                                         |
| :-------------------- | :---------------------------------------------------------------------------------------------------------------- |
| **macOS**             | **Recomendado:** Usa el gestor de paquetes **Homebrew** para obtener la versión más reciente: `brew install git`. |
| **Windows**           | Descargar e instalar desde el instalador oficial de [git-scm.com](https://git-scm.com/download/win).              |
| **Linux**             | Utiliza el gestor de paquetes (ej. Debian/Ubuntu): `sudo apt-get install git`.                                    |

> ℹ️ **Verificación:** Una vez instalado, verifica la versión en tu Terminal: `git --version`.

Te debe salir la versión actual que estás usando.

![Version de Git en Mac OS](<assets/Fundamentos/assets/Version\ de\ Git\ en\ macOs.png>)

### 2.2. Preparación del Entorno y Repositorio Local

#### 2.2.1. Comandos de Terminal Esenciales

| Comando          | Propósito                                  | Ejemplo de Uso         |
| :--------------- | :----------------------------------------- | :--------------------- |
| `cd [carpeta]`   | Cambiar de directorio (navegar).           | `cd ~/Proyectos`       |
| `ls`             | Listar el contenido del directorio actual. |                        |
| `mkdir [nombre]` | Crear un nuevo directorio (carpeta).       | `mkdir mi-primer-repo` |

#### 2.2.2. Inicialización del Proyecto

Sigue estos pasos para crear tu primer repositorio local.

| Paso                    | Comando (Terminal) | Propósito y Explicación                                                                                     |
| :---------------------- | :----------------- | :---------------------------------------------------------------------------------------------------------- |
| **1. Crear Carpeta**    | `mkdir hello-git`  | Crea la carpeta del proyecto.                                                                               |
| **2. Entrar a Carpeta** | `cd hello-git`     | Navega al directorio.                                                                                       |
| **3. Inicializar Git**  | `git init`         | **¡Clave!** Este comando crea la subcarpeta oculta `.git/` y convierte el directorio en un repositorio Git. |

![Comando git init desde terminal](assets/hello-git.png)

> Opcional: Abrir desde terminal el Editor con el comando `code .` (requiere VS Code)

### 2.3. Configuración de Credenciales

Antes de hacer _commits_, debes decirle a Git quién eres para que tus contribuciones sean atribuidas correctamente.

| Configuración | Comando                                         | Explicación                                                               |
| :------------ | :---------------------------------------------- | :------------------------------------------------------------------------ |
| **Nombre**    | `git config --global user.name "Tu Nombre"`     | Define el nombre que aparecerá como autor en todos tus commits.           |
| **Correo**    | `git config --global user.email "tu@email.com"` | Define el email asociado a tus commits (debe coincidir con el de GitHub). |

![Configuracion de user](assets/user-git-hub.png)

> 📌 **Nota sobre `--global`:** Esta bandera aplica la configuración a **todos** tus futuros proyectos. Si omites `--global`, la configuración solo aplica al repositorio actual.

#### 2.3.4. El Archivo `.gitconfig`

La configuración global se guarda en el archivo **`.gitconfig`** ubicado en tu directorio principal (`~/`). Puedes verificar su contenido ejecutando `cat ~/.gitconfig`.

---

<a id="3-buenas-prácticas-mensajes-de-commit"></a>

## 📖 3. Buenas Prácticas: Mensajes de Commit

Los mensajes de commit deben ser claros y concisos. Utilizamos el estándar **Conventional Commits** para mantener un historial legible y profesional.

**Formato del Mensaje:**

<tipo>(ámbito opcional): <descripción breve>

| Tipo           | Propósito                                                         | Ejemplo Práctico (Descripción)                                 |
| :------------- | :---------------------------------------------------------------- | :------------------------------------------------------------- |
| **`feat`**     | **Nuevas Funcionalidades.** (Feature)                             | `feat: Agregada validación de input en formulario de registro` |
| **`fix`**      | **Corrección de Errores.** (Bug)                                  | `fix: Corregido error que causaba crash al cerrar sesión`      |
| **`docs`**     | **Documentación.** (READMEs, comentarios, guías)                  | `docs: Actualizada la tabla de comandos esenciales`            |
| **`style`**    | **Estilo/Formato.** (Espacios, punto y coma, presentación visual) | `style: Actualizada imagen de portada a formato horizontal`    |
| **`refactor`** | **Refactorización.** (Mejora de estructura sin cambio de lógica)  | `refactor: Simplificada la lógica de la función de parseo`     |
| **`test`**     | **Pruebas.** (Añadir o corregir tests)                            | `test: Añadidos tests unitarios para la función de login`      |
| **`chore`**    | **Mantenimiento.** (Configuración, `.gitignore`, dependencias)    | `chore: Agregada regla .DS_Store al .gitignore`                |

---

<a id="4-comandos-básicos-de-git-módulo-i"></a>

## 📝 4. Comandos Básicos de Git

| Comando                                | Descripción                                                              |
| :------------------------------------- | :----------------------------------------------------------------------- |
| `git --version`                        | Muestra la versión de Git instalada.                                     |
| `git config --global user.name "..."`  | Establece el nombre de autor global.                                     |
| `git config --global user.email "..."` | Establece el correo de autor global.                                     |
| `git init`                             | Inicializa un nuevo repositorio de Git.                                  |
| `git rm -r --cached .DS_Store`         | Detiene el rastreo de archivos del sistema que fueron subidos por error. |

---

## 🚀 Próximo Paso: Módulo II

El Módulo II se centrará en el manejo del flujo de trabajo esencial: el ciclo **`git add`** $\rightarrow$ **`git commit`** $\rightarrow$ **`git log`** y el manejo de ramas (`git branch`).
