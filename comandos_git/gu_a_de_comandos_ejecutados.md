# Guía y Referencia de Comandos Ejecutados

En este documento encontrarás la clasificación y explicación técnica de todos los comandos registrados en tu historial de terminal. Se encuentran agrupados por herramientas: **Git**, **Navegación y Sistema (Bash/Linux)**, **Gestor de Entornos Python (`uv`)**, y **Herramientas Externas (SSH y VS Code)**.

---

## 1. Comandos de Git

Git es el sistema de control de versiones distribuido que utilizas para rastrear los cambios en tu código fuente.

### 1.1 Configuración (`git config`)

| Comando base / Sintaxis | Ejemplo de tu historial | Descripción y funcionamiento |
| :--- | :--- | :--- |
| `git --version` | `git --version` | Muestra la versión de Git instalada en el sistema. |
| `git config --global user.name "<nombre>"` | `git config --global user.name "lafavorita-jh"` | Establece tu nombre de autor de forma global en tu máquina. Se asocia a todos los commits futuros. |
| `git config --global user.email "<correo>"` | `git config --global user.email "lafavoritasti@gmail.com"` | Configura el correo electrónico asociado a tus commits. Si ejecutas `git config --global user.email` sin comillas, simplemente consulta el valor configurado actualmente. |
| `git config --global --list` | `git config --global --list` | Lista todos los pares clave-valor configurados a nivel global en el archivo `~/.gitconfig`. |
| `git config --global init.defaultBranch <rama>` | `git config --global init.defaultBranchh main` *(nota el typo)* | Define el nombre por defecto de la rama principal al inicializar repositorios (por defecto suele ser `master` o `main`). |

---

### 1.2 Flujo de Trabajo Básico (Creación, Estado y Commits)

| Comando base / Sintaxis | Ejemplo de tu historial | Descripción y funcionamiento |
| :--- | :--- | :--- |
| `git init` | `git init` | Inicializa un nuevo repositorio Git creando la carpeta oculta `.git/` en el directorio actual. |
| `git status` | `git status` | Muestra el estado del árbol de trabajo: archivos rastreados, modificados, en el área de preparación (*staging*) o no rastreados (*untracked*). |
| `git add <ruta>` | `git add comandos_git/comandos_linux.txt`<br>`git add .gitignore` | Añade los cambios de archivos o carpetas específicas al área de preparación (*staging area* o *index*), dejándolos listos para el próximo commit. |
| `git commit -m "<mensaje>"` | `git commit -m "inicialicé el archivo comandos linux"` | Guarda una instantánea permanente (*snapshot*) de los cambios que están en *staging*, acompañada de un mensaje descriptivo (`-m`). |
| `git commit -am "<mensaje>"` | `git commit -am "Pongo ejemplos de variables"` | **Atajo:** añade automáticamente todos los archivos ya rastreados que han sido modificados al staging y realiza el commit al mismo tiempo. No incluye archivos nuevos sin rastrear (*untracked*). |
| `git restore <archivo>` | `git restore comandos_git/comandos_linux.txt` | Descarta los cambios locales en el directorio de trabajo sobre un archivo rastreado, volviéndolo al estado del último commit. |
| `git log` | `git log` | Muestra el historial completo de commits (autor, fecha, hash SHA-1 completo y mensaje). |
| `git log --oneline` | `git log --oneline` | Muestra una versión compacta del historial, resumiendo cada commit en una sola línea con un hash abreviado y el mensaje. |

---

### 1.3 Ramas y Fusión (*Branches & Merging*)

| Comando base / Sintaxis | Ejemplo de tu historial | Descripción y funcionamiento |
| :--- | :--- | :--- |
| `git branch` | `git branch` | Lista todas las ramas locales existentes en el repositorio actual. La rama activa aparece marcada con un asterisco `*`. |
| `git branch -M <nuevo_nombre>` | `git branch -M main` | Renombra forzosamente la rama actual al nombre especificado (usado habitualmente para pasar de `master` a `main`). |
| `git branch -d <nombre_rama>` | `git branch -d monandos` | Elimina una rama local de forma segura (solo si sus cambios ya fueron fusionados con otra rama). |
| `git switch <nombre_rama>` | `git switch main` | Cambia tu espacio de trabajo a una rama local existente. |
| `git switch -c <nueva_rama>` | `git switch -c ft_jhunior` | Crea una rama nueva y se posiciona en ella inmediatamente (equivalente tradicional de `git checkout -b <nombre>`). |
| `git merge <rama>` | `git merge monandos_git` | Integra el historial y los cambios de la rama indicada dentro de la rama en la que te encuentras posicionado actualmente. |

---

### 1.4 Repositorios Remotos y Sincronización

| Comando base / Sintaxis | Ejemplo de tu historial | Descripción y funcionamiento |
| :--- | :--- | :--- |
| `git remote add <nombre> <url>` | `git remote add origin https://github.com/lafavorita-jh/dataengineer-g1.git` | Vincula tu repositorio local con un repositorio remoto en la web (en este caso GitHub), asignándole el alias convencional `origin`. |
| `git push -u <remoto> <rama>` | `git push -u origin main`<br>`git push -u origin ft_jhunior` | Sube los commits locales a la rama remota y la opción `-u` (*upstream*) vincula permanentemente ambas ramas para que en el futuro solo tengas que escribir `git push`. |
| `git push` | `git push` | Envía los commits locales al repositorio y rama remota previamente configurada como upstream. |

---

## 2. Comandos de Terminal / Sistema (Bash, Linux, Git Bash)

Comandos estándar utilizados para desplazarse por el sistema de archivos de tu computadora y gestionar archivos.

| Comando base / Sintaxis | Ejemplo de tu historial | Descripción y funcionamiento |
| :--- | :--- | :--- |
| `pwd` | `pwd` | *Print Working Directory*: Imprime en pantalla la ruta absoluta de la carpeta en la que te encuentras posicionado. |
| `cd <ruta>` | `cd C:/Users/hp/OneDrive/Ing_Datos`<br>`cd D:/`<br>`cd /d/` | *Change Directory*: Cambia la carpeta de trabajo actual a la ruta especificada. Permite rutas de Windows (`D:/`) o formato Unix (`/d/`). |
| `cd ..` | `cd ..` | Sube un nivel en el árbol de directorios (regresa a la carpeta padre). |
| `mkdir <carpeta>` | `mkdir dataengineer-g1` | *Make Directory*: Crea una nueva carpeta con el nombre proporcionado. |
| `&&` *(Operador)* | `mkdir comandos_git && cd comandos_git` | Encadenador lógico: ejecuta el segundo comando únicamente si el primero terminó exitosamente. |
| `ls` | `ls` | *List*: Enumera los archivos y subcarpetas contenidos en el directorio actual. |
| `ls -la` | `ls -la` | Lista archivos con detalles de permisos, tamaño y fecha (`-l`), e incluye archivos y carpetas ocultas (`-a`, los que empiezan con punto como `.git` o `.gitignore`). |
| `rm -rf <carpeta>` | `rm -rf fundamentos_python` | *Remove*: Borra de forma recursiva (`-r`) y forzosa (`-f`) carpetas y su contenido sin pedir confirmación. |
| `history \| tail -n <número>` | `history \| tail -n 30` | Muestra el historial de comandos ejecutados, pasando la salida por una tubería (`\|`) hacia `tail -n 30` para ver solo los últimos 30 comandos. |
| `exit` | `exit` | Finaliza y cierra la sesión actual de la terminal. |

---

## 3. Gestor de Proyectos Python: `uv`

`uv` es un administrador de paquetes y proyectos de Python moderno y ultrarrápido (desarrollado en Rust por Astral, creadores de Ruff).

| Comando base / Sintaxis | Ejemplo de tu historial | Descripción y funcionamiento |
| :--- | :--- | :--- |
| `uv init <nombre> --python <versión>` | `uv init fundamentos_python --python 3.14` | Inicializa un nuevo proyecto Python estructurado, descargando o asociando la versión de Python solicitada (por ejemplo, Python 3.14). |
| `uv init --no-package <nombre>` | `uv init --no-package fundamentos-python` | Crea un proyecto Python configurado como aplicación independiente o scripts, sin preparar el proyecto como paquete distribuible en PyPI. |
| `uv run <archivo.py>` | `uv run main.py` | Ejecuta un script dentro del entorno virtual gestionado automáticamente por `uv`, asegurando que todas las dependencias estén sincronizadas. |
| `uv add <paquete>` | `uv add ipykernel`<br>`uv add numpy` | Descarga e instala paquetes en el entorno del proyecto y los registra automáticamente en el archivo de configuración `pyproject.toml`. |

---

## 4. Conectividad y Editores

| Comando | Ejemplo de tu historial | Descripción y funcionamiento |
| :--- | :--- | :--- |
| `code .` | `code .` | Abre el editor **Visual Studio Code** teniendo como raíz de trabajo la carpeta actual (`.`). |
| `ssh -T git@github.com` | `ssh -T git@github.com` | Prueba la conexión y autenticación por clave SSH con los servidores de GitHub. El parámetro `-T` desactiva la asignación de terminal interactiva (útil para diagnósticos). |

---

## 5. Análisis de Errores Comunes Detectados en el Historial

Durante tu sesión se presentaron algunos errores tipográficos que la terminal rechazó. Comprenderlos te ayudará a afianzar la sintaxis:

1. **Typo en configuración:**
   * Ejecutado: `git config --global init.defaultBranchh main`
   * Causa: `defaultBranchh` tiene doble `h`. Git no reconoció la clave correcta, que es `init.defaultBranch`.
2. **Typos en subcomandos de Git:**
   * `git statud` y `git --status`: El comando correcto no lleva guiones ni termina en "d", es simplemente `git status`.
   * `git ad`: El comando es `git add`.
   * `git log --online`: La opción correcta para ver el registro en una línea es `--oneline` (una línea), no *online*.
3. **Sintaxis incompleta de Commit:**
   * `git commit "Cree el archivo ft_jhunior.txt"`: Faltó el indicador `-m` antes del texto.
   * `git -am "operadores logicos"`: Faltó especificar la acción `commit` entre `git` y el flag `-am`.
4. **Navegación pegada o duplicada:**
   * `cd/d`: Faltó un espacio entre el comando `cd` y la ruta `/d`.
   * `cd cd fundamentos-python/`: Se repitió la palabra `cd`.
5. **Nombres de ramas con errores:**
   * Creaste la rama `monandos_git` en lugar de `comandos_git`, por lo que al intentar hacer `git merge comandos_git` Git avisó que la rama no existía hasta que usaste el nombre con el que la habías creado.