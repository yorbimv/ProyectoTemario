# 🔰 Módulo I:

## Fundamentos y Configuración Inicial (Lecciones 1-6)

Este módulo cubre los cimientos teóricos del control de versiones, la importancia de Git/GitHub en el desarrollo profesional y los primeros pasos para la configuración del entorno.

| Lección                                                                 | Título               | Conceptos Clave                                                               | Comandos / Notas                                                               |
| :---------------------------------------------------------------------- | :------------------- | :---------------------------------------------------------------------------- | :----------------------------------------------------------------------------- |
| [Introducción](#1-introducción-la-importancia-del-control-de-versiones) | Introducción         | Propósito del curso y control de versiones.                                   | ¿Que es Git? github?, Primeros pasos                                           |
| **L1**                                                                  | Introducción a Git   | Definición de Git (DVCS), diferencia con otras herramientas.                  | Comienza la parte de Git.                                                      |
| **L2**                                                                  | Historia de Git      | Contexto histórico y creación de Git por Linus Torvalds.                      |                                                                                |
| **L3**                                                                  | Instalación de Git   | Proceso de instalación en diferentes sistemas operativos (Mac/Linux/Windows). | Verificar instalación: `git --version`.                                        |
| **L4**                                                                  | Comandos Terminal    | Navegación básica (`cd`, `ls`, `mkdir`), fundamentos de la línea de comandos. | Prerrequisito esencial.                                                        |
| **L5**                                                                  | Configuración de Git | Establecer la identidad del usuario para los _commits_.                       | `git config --global user.name "..."`, `git config --global user.email "..."`. |
| **L6**                                                                  | `git init`           | Inicializar un repositorio local.                                             | `git init` (Crea la carpeta `.git`).                                           |

---

## 🚩 1. Introducción: La Importancia del Control de Versiones

### 1.1. ¿Qué es Git?

**Git** es el **Sistema de Control de Versiones Distribuido (DVCS)** más popular del mundo. Es un software que se instala localmente en tu computadora.

- **Función Principal:** Rastrear y registrar cada cambio realizado en tus archivos a lo largo del tiempo.
- **Beneficio Clave:** Permite volver a cualquier versión anterior de tu código con precisión, actúa como una "máquina del tiempo" para tu proyecto.

### 1.2. ¿Qué es GitHub?

**GitHub** es una **Plataforma de Alojamiento Web** que utiliza la tecnología Git. Es un servicio en la nube donde almacenas tus repositorios remotos.

- **Función Principal:** Proporcionar un lugar centralizado para el almacenamiento (backup), la colaboración, la gestión de proyectos y la revisión de código.
- **Diferencia:** **Git** es la herramienta (el motor); **GitHub** es el servicio (la plataforma social).

### 1.3. Importancia en la Programación

El uso de Git y GitHub es un **estándar de la industria** por las siguientes razones:

- **Colaboración:** Permite que múltiples desarrolladores trabajen en el mismo código sin sobrescribirse.
- **Integridad del Código:** Protege la versión principal del proyecto mediante flujos de trabajo controlados (_branches_ y _Pull Requests_).
- **Portafolio Profesional:** Tu perfil de GitHub funciona como tu currículum de código, mostrando tus habilidades y proyectos activos a reclutadores.

---

## ⚙️ 2. Primeros Pasos y Configuración

### 2.1. Instalación y Descargas

Para empezar, necesitas tener Git instalado en tu sistema.

| Sistema Operativo         | Enlace de Descarga / Método Recomendado                                                                              |
| :------------------------ | :------------------------------------------------------------------------------------------------------------------- |
| **macOS**                 | Viene preinstalado. **Recomendado:** Utilizar **Homebrew** para obtener la versión más reciente: `brew install git`. |
| **Windows**               | Descargar el instalador oficial de [git-scm.com](https://git-scm.com/download/win).                                  |
| **Linux (Debian/Ubuntu)** | A través del gestor de paquetes (`sudo apt-get install git`).                                                        |

### 2.2. Inicialización de un Repositorio (Ejemplos)

Para empezar, necesitas tener Git instalado en tu sistema.

| Sistema Operativo         | Enlace de Descarga / Método Recomendado                                                                          |
| :------------------------ | :--------------------------------------------------------------------------------------------------------------- |
| **macOS**                 | Viene preinstalado. Si no, se instala al ejecutar `git` por primera vez o con **Homebrew** (`brew install git`). |
| **Windows**               | Descargar el instalador oficial de [git-scm.com](https://git-scm.com/download/win).                              |
| **Linux (Debian/Ubuntu)** | A través del gestor de paquetes (`sudo apt-get install git`).                                                    |

### 2.2. Inicialización de un Repositorio (Ejemplos)

Hay dos formas de iniciar un proyecto con Git:

| Método               | Descripción                                         | Comando (Mac / Windows / Linux) |
| :------------------- | :-------------------------------------------------- | :------------------------------ |
| **Iniciación Local** | Creas la carpeta localmente y la preparas para Git. | **`git init`**                  |
| **Desde la Web**     | Creas el repositorio en GitHub y lo descargas.      | **`git clone [URL]`**           |

### 2.3. Configuración Inicial Práctica (L5 y L6)

Antes de empezar a trabajar en un proyecto, debemos configurar tu identidad y crear el espacio de trabajo.

#### 2.3.1. Preparación del Entorno (Mac Terminal)

| Paso                    | Comando (Terminal de Mac) | Propósito                                                                                     |
| :---------------------- | :------------------------ | :-------------------------------------------------------------------------------------------- |
| **1. Crear Carpeta**    | `mkdir hello-git`         | Crea una nueva carpeta para el primer proyecto.                                               |
| **2. Entrar a Carpeta** | `cd hello-git`            | Navega al directorio recién creado.                                                           |
| **3. Inicializar Git**  | `git init`                | Convierte la carpeta `hello-git` en un repositorio de Git (crea el archivo oculto `.git`).    |
| **4. Abrir en Editor**  | `code .`                  | **(Requiere VS Code)** Abre la carpeta actual en Visual Studio Code para empezar a codificar. |

#### 2.3.2. Software Requerido

| Software               | Descripción                      | Enlace de Descarga                                      |
| :--------------------- | :------------------------------- | :------------------------------------------------------ |
| **Git**                | Sistema de control de versiones. | [git-scm.com](https://git-scm.com/downloads)            |
| **Terminal**           | Línea de comandos de macOS.      | (Preinstalada)                                          |
| **Visual Studio Code** | Editor de código recomendado.    | [code.visualstudio.com](https://code.visualstudio.com/) |

#### 2.3.3. Configurar Identidad de Git

Debes decirle a Git quién eres para que tus _commits_ queden correctamente atribuidos. Esta configuración es persistente.

| Configuración          | Comando (Dentro de `hello-git`)                 | Explicación                                                                       |
| :--------------------- | :---------------------------------------------- | :-------------------------------------------------------------------------------- |
| **Nombre de Usuario**  | `git config --global user.name "Tu Nombre"`     | Define el nombre que aparecerá como autor en todos tus commits.                   |
| **Correo Electrónico** | `git config --global user.email "tu@email.com"` | Define el email asociado a tus commits. Debe coincidir con el que usas en GitHub. |

> **¿Por qué se usa `--global`?**
> La opción `--global` indica que esta configuración (nombre y email) se aplicará a **todos** los proyectos de Git que inicies o clones en tu máquina. Esto evita tener que configurar tu identidad repetidamente en cada nuevo repositorio. Si omitieras `--global`, la configuración solo aplicaría al repositorio actual (`hello-git`).

#### 2.3.4. El Archivo `.gitconfig`

Al usar `git config --global`, Git guarda esta información en un archivo de configuración central:

- **Ubicación:** Se crea un archivo llamado **`.gitconfig`** en tu directorio principal (`~/`).
- **Función:** Sirve como el registro permanente de tus preferencias globales de Git, incluyendo tu nombre, email, y alias personalizados (`git alias`).
- **Visualización:** Puedes ver su contenido ejecutando: `cat ~/.gitconfig`

---

## 📝 3. Comandos Básicos de Git (Módulo I)

Estos comandos son esenciales para empezar a usar Git y se ejecutan en la **Terminal** (Mac/Linux) o **Git Bash** (Windows).

| Comando                          | Descripción Breve                                              | ¿Cómo se usa?                                   | Lección |
| :------------------------------- | :------------------------------------------------------------- | :---------------------------------------------- | :------ |
| `git --version`                  | Muestra la versión de Git instalada.                           | Verifica la instalación.                        | L3      |
| `git config --global user.name`  | Establece tu nombre de autor global.                           | `git config --global user.name "Tu Nombre"`     | L5      |
| `git config --global user.email` | Establece tu correo de autor global.                           | `git config --global user.email "tu@email.com"` | L5      |
| `git init`                       | Inicializa un nuevo repositorio de Git.                        | Ejecutar en la carpeta raíz del proyecto.       | L6      |
| `cd [carpeta]`                   | **Comando de Terminal:** Navegar a un directorio.              | `cd ~/Proyectos`                                | L4      |
| `ls`                             | **Comando de Terminal:** Listar el contenido de un directorio. |                                                 | L4      |

---

## 🗺️ 4. Temario Cubierto (Lecciones 1-6)

Este sub-módulo abordó las siguientes lecciones del temario principal:

- **Lección 1:** Introducción a Git
- **Lección 2:** Historia de Git
- **Lección 3:** Instalación de Git
- **Lección 4:** Comandos básicos de la terminal
- **Lección 5:** Configuración de Git
- **Lección 6:** `"git init"`

---

## 🚀 Próximo Paso en el Curso:

El Módulo II se centrará en el manejo de ramas (`git branch`), el flujo de trabajo esencial (`git add`, `git commit`) y la manipulación del historial.

---
