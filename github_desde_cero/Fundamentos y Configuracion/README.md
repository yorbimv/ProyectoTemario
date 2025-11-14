# 🔰 Módulo I: Fundamentos y Configuración Inicial (Lecciones 1-6)

Este módulo cubre los cimientos teóricos del control de versiones, la importancia de Git/GitHub en el desarrollo profesional y los primeros pasos para la configuración del entorno.

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

## 3. Comandos para Sincronizar (Terminal de Mac)

Una vez que guardes el contenido en el archivo, debes subirlo a tu rama de trabajo:

```bash
# Asegúrate de estar en el directorio raíz (ProyectoTemario)
cd ~/Proyectos/ProyectoTemario

# 1. Prepara la nueva carpeta y el archivo
git add .

# 2. Guarda los cambios con un mensaje claro
git commit -m "docs: Agregado modulo 1 de GitHub con fundamentos y configuracion"

# 3. Sube los cambios a la rama remota
git push origin github_desde_cero
```
