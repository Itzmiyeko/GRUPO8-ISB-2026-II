# LAB 01: Introducción a Github
## 1. Diferencia entre Git y Github
### **Git** 
Es un sistema de control desarrollado inicialmente por Linus Torvalds en 2005. Este se basa en un software que se instala localmente en el equipo del programador y que gestiona las versiones actualizadas del código de que suele permitir distintas funciones:
- Registrar los cambios hecho en un grupo de archivos.
- Desarrollar branches para realizar funcionalidades de manera aislada.
- Fusionar cambios originados de distintas líneas de programación.
- Revertir el proyectos a versiones pasadas.
- Trabajar localmente (en el disco C:), sin necesidad del acceso a Internet.

### **Github** 
Es una plataforma de alojamiento en la nube que usa Git como motor subyacente, incluida en ella una serie de capas de servicios adicionales: 
- Repositorios remotos accesibles.
- Tools de gestión de proyectos, como cronogramas, tableros Kanban, milestones, etc.
- Revisión de códigos
- Integración de flujos de automatización
- Controles de accesos y permisos a repositorios.

En consecuencia, mientras que Git puede utilizarse de manera completamente independiente sin necesidad de GitHub, GitHub no podría existir sin Git, ya que depende de él para gestionar el versionado de los proyectos que aloja. Existen, además, plataformas alternativas que cumplen una función similar a GitHub, como GitLab o Bitbucket, todas ellas construidas sobre la base de Git.

### Instalación y configuración inicial de Git

Antes de comenzar a utilizar Git, este debe instalarse en el sistema operativo correspondiente:

- **Windows**: descargar el instalador desde [git-scm.com](https://git-scm.com/).
- **Linux**: `sudo apt-get install git`
- **macOS**: `brew install git`

Para la verificación de que la instalación se realizó correctamente, se usan estas líneas de código:

```bash
git --version
```

### Áreas de trabajo de Git

Para comprender el funcionamiento interno de Git, es útil visualizar el flujo de un proyecto a través de cuatro áreas o estados:

1. **Directorio de trabajo (Working Directory)**: lugar donde se modifican y crean los archivos del proyecto de manera cotidiana.
2. **Área de preparación (Staging Area)**: es el espacio intermedio donde se sitúan los cambios que se desean incluir en el próximo commit, mediante el comando `git add`.
3. **Repositorio local (Local Repository)**: constituye la copia del proyecto almacenada en el equipo, junto con todo su historial de cambios confirmados mediante `git commit`.
4. **Repositorio remoto (Remote Repository)**: es la versión compartida del proyecto alojada en GitHub, hacia la cual se envían los cambios mediante `git push`, y desde la cual se descargan actualizaciones mediante `git pull` o `git fetch`.

## 2. COMANDOS PRINCIPALES
Los comandos fundamentales que conforman el flujo de trabajo por medio de Git para poder editar en Github:
* **git init:** inicia el rastreo de historial de edits en un repositorio, conviertiéndolo en uno local de Git.
* **git add:** agrega todos los cambios realizados al área de trabajo, es decir, selecciona que modificaciones se incluirán en el próximo registro de cambios.
* **git commit:** representa el último guardado en el repositorio local.
* **git push:** sube los cambios confirmados (commits) desde el repositorio local hacia GitHub, es decir, traslada la información de local a remoto.
* **git pull:** descarga los cambios que se encuentren en línea, ya sea porque fueron subidos desde otro equipo propio o por otros colaboradores del proyecto, e integra dichos cambios al entorno local.
* **git status:** muestra el estado actual de los archivos del repositorio, mostrando cuales líneas han sido editadas, cuáles están en el área de preparación y cuáles aún no han sido registrados. Su propósito es verificar el estado del proyecto antes de realizar un commit.

Primero se edita el archivo, luego se agrega al área de preparación, después se confirma el cambio con un mensaje descriptivo, y finalmente se sube al repositorio remoto en GitHub:
**Flujo:** git init → Modificar → git add → git commit → git push → GitHub

### Curiosidades
#### Git status
Nos proporciona la información de cuáles archivos han cambiado, cuáles ya están preparados (*staged*) y cuáles aún no son rastreados por Git. Se recomienda utilizarlo con frecuencia, especialmente después de crear o modificar un archivo, ya que permite confirmar el estado exacto del proyecto antes de continuar:

```bash
git status
git status -s     # versión resumida (--short)
```

Un flujo típico de trabajo sería:

```bash
git status
git add <archivo>
git commit -m "Descripción del cambio"
```

#### Git log
git log muestra el historial completo de commits realizados en el repositorio, permitiendo revisar quién hizo cada cambio y cuándo:

```bash
git log                                  # historial detallado
git log --oneline                        # vista compacta
git log --oneline --graph --decorate --all   # vista gráfica de ramas y fusiones
```


## 3. MANEJO DESDE VISUAL STUDIO CODE
Visual Studio Code permite ejecutar todo este flujo de trabajo de manera visual, sin necesidad de escribir los comandos manualmente en la terminal, a través del panel de "Control de código fuente". El orden recomendado de trabajo es el siguiente:

1. Pull: antes de comenzar a trabajar, se recomienda actualizar el repositorio local descargando los cambios más recientes del repositorio remoto, evitando así conflictos posteriores.
2. Add (nueva modificación): una vez realizados los cambios en los archivos, estos se agregan al área de preparación seleccionándolos desde el panel de control de código fuente.

<div align="center">
<img width="500" height="136" alt="p1" src="https://github.com/user-attachments/assets/550e088e-faee-4282-adf8-97d39bdc7a84" />
</div>

3. Commit con descripción: se redacta un mensaje que explique el cambio realizado y se confirma el registro, quedando guardado en el historial local del proyecto.
<div align="center">
<img width="500" height="136" alt="p2" src="https://github.com/user-attachments/assets/2785e1f9-c718-4199-9564-aaf662f40405" />
</div>

4. Push: Sincronización: finalmente, se sincronizan los cambios confirmados, enviándolos al repositorio remoto en GitHub para que queden disponibles en línea.
<div align="center">
<img width="500" height="136" alt="p3" src="https://github.com/user-attachments/assets/e8cfe533-ce4b-4dc4-9ac1-9389f8d9af85" />
</div>


### Vincular Visual Studio Code con GitHub mediante GitHub CLI

Antes de publicar un repositorio desde Visual Studio Code, es posible autenticar la cuenta de GitHub directamente desde la terminal utilizando la herramienta **GitHub CLI** (`gh`), disponible en [cli.github.com](https://cli.github.com/). El proceso es el siguiente:

```bash
gh auth login
```

Este comando inicia un asistente interactivo que solicitará, entre otras cosas:

- Seleccionar la cuenta (**GitHub.com** o GitHub Enterprise Server).
- Elegir el protocolo preferido para las operaciones de Git (**HTTPS** o **SSH**).
- Confirmar la autenticación de Git con las credenciales de GitHub.
- Seleccionar el método de autenticación mediante navegador web.

Al elegir la autenticación por navegador, la terminal generará un código temporal de un solo uso, el cual debe copiarse e ingresarse en la página que se abrirá automáticamente, autorizando finalmente el acceso. Una vez completado el proceso, la terminal mostrará un mensaje confirmando el inicio de sesión exitoso.

### Activar el envío automático (auto-push) tras cada commit

Visual Studio Code permite configurar que cada commit se envíe automáticamente al repositorio remoto, sin necesidad de presionar "Push" manualmente:

1. Abre la configuración (`Ctrl + ,`).
2. Busca la opción **"Post Commit Command"**.
3. Establece el valor de **Git › Post Commit Command** en `push`.

De esta manera, cada vez que se realice un commit, este se sincronizará automáticamente con GitHub, evitando el paso adicional de sincronización manual. De forma complementaria, puede activarse la opción **"Git: Autofetch"**, la cual permite que Visual Studio Code descargue periódicamente las actualizaciones del repositorio remoto en segundo plano.

## 4. BUENAS PRÁCTICAS
Se recomienda un uso ordenado del flujo de trabajo descrito, se recomienda considerar:
* **CONFIGURACION INICIAL:**
Antes de realizar cualquier modificación al repositorio remoto, es indispensable configurar la identidad del usuario en Git, mediante los siguientes comandos:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

* **CREACIÓN DE UN REPOSITORIO:**
  Existen dos enfoques posibles:

  *a) Crear el repositorio primero en GitHub:*
  Se accede a la plataforma, se selecciona la opción "New repository", se asigna un nombre, una descripción opcional y se define su visibilidad (público o privado). Posteriormente, dicho repositorio remoto se clona hacia el equipo local mediante Visual Studio Code, utilizando la opción "Clone Repository" desde el panel de control de código fuente, o bien mediante el comando:

  ```bash
  git clone https://github.com/usuario/nombre-repositorio.git
  ```

   *b) Crear el repositorio primero de forma local:*
   Se inicializa el proyecto dentro de Visual Studio Code y, posteriormente, se vincula a un repositorio remoto en GitHub mediante:

    ```bash
    git init
    git remote add origin https://github.com/usuario/nombre-repositorio.git
    ```

* **CREACIÓN DE RAMAS:**
Las ramas, también llamadas branchs, permiten que varias personas trabajen simultáneamente sobre un mismo proyecto sin interferir entre sí. Se recomienda que el líder del equipo sea quien decida qué versión final se integrará a la rama principal, evitando así tener que lidiar con conflictos de fusión (merge conflicts) causados por modificaciones simultáneas sobre las mismas líneas de código.
Visual Studio Code permite gestionar ramas de manera completamente visual, sin necesidad de recurrir a comandos de terminal como `git branch` o `git checkout`.

  **Opción 1: Mediante el selector de ramas (barra inferior)**
  
  1. **Ubica el selector de ramas**: en la esquina inferior izquierda de la ventana de VS Code, encontrarás un ícono con el nombre de la rama actual (generalmente `main` o `master`), acompañado de un pequeño ícono de rama.
  2. **Haz clic sobre dicho selector**: se desplegará un menú en la parte superior de la pantalla con la lista de ramas existentes en el repositorio.
  3. **Selecciona "Create new branch..."**: esta opción aparecerá en la parte superior del listado desplegado.
  4. **Asigna un nombre a la rama**: se recomienda utilizar nombres descriptivos y sin espacios, por ejemplo: `feature-login`, `fix-bug-formulario` o `desarrollo-modulo2`. Escribe el nombre y presiona `Enter`.
  5. **Verifica el cambio**: automáticamente, Visual Studio Code cambiará el entorno de trabajo hacia la nueva rama creada, lo cual se refleja en el selector inferior izquierdo.
  
  **Opción 2: Mediante el panel de Control de código fuente**
  
  1. Abre el panel de **"Control de código fuente"**.
  2. Haz clic en los **tres puntos (...)** ubicados en la parte superior del panel.
  3. Dirígete a la opción **"Branch"** dentro del menú desplegado.
  4. Selecciona **"Create Branch..."** e ingresa el nombre correspondiente.
  
  **Equivalente por línea de comandos:**
  
  ```bash
  git branch nueva-rama          # crea la rama sin cambiarse a ella
  git checkout -b nueva-rama     # crea la rama y se cambia a ella en un solo paso
  git checkout main              # cambia hacia una rama existente
  ```
  
  Para listar las ramas disponibles:
  
  ```bash
  git branch        # lista las ramas locales
  git branch -vv     # muestra la rama remota asociada a cada rama local
  git branch -r      # lista solo las ramas remotas
  git branch -a      # lista ramas locales y remotas
  ```
  
  Para eliminar una rama:
  
  ```bash
  git branch -d nombre-rama    # eliminación segura (falla si hay cambios sin fusionar)
  git branch -D nombre-rama    # eliminación forzada
  ```
  **Fusión simple (fast-forward)**, cuando `main` no ha recibido cambios nuevos desde que se creó la rama secundaria:
  
  ```bash
  git switch main
  git pull --ff-only
  git merge nueva-rama
  git push
  ```
  
  **Fusión con commit de fusión** (común en equipos de trabajo), cuando `main` y la rama secundaria han recibido commits nuevos de forma independiente:
  
  ```bash
  git switch main
  git pull
  git merge nueva-rama
  git push
  ```
  **Trabajo con ramas remotas existentes**
  
  Cuando un repositorio remoto ya cuenta con varias ramas creadas por otros integrantes del equipo, se puede sincronizar entre ellas y comenzar a trabajar sobre ellas desde el equipo local siguiendo estos pasos:
  
  ```bash
  git branch -a                                      # 1. Verificar ramas locales y remotas
  git fetch --all                                     # 2. Actualizar referencias remotas
  git pull --ff-only                                  # 3. Descargar e integrar últimos cambios
  git switch --track -c nombre-rama origin/nombre-rama # 4. Crear rama local que siga a una remota
  git branch -vv                                      # 5. Verificar qué rama remota sigue cada rama local
  ```

* **Extensión "Markdown Preview Enhanced":**
  Se recomienda instalar esta extensión, ya que permite visualizar una vista previa de cómo se verá el documento renderizado antes de subirlo al repositorio. Dicha vista previa puede activarse mediante el atajo de teclado Ctrl + k, luego se sueltan ambas teclas e inmediatamente después presionar la tecla y.
  
  Lo que podemos decir es que Visual Studio Code funciona como el intermediario visual que resume la ejecución de comandos por Git, , sin eliminar la necesidad de comprender los conceptos subyacentes, los cuales resultan muy esencial e ineludible para un uso eficaz en proyectos de mayor complejidad.
  Además, cuando dos o más colaboradores modifican simultáneamente las mismas líneas de un archivo en el repositorio, Git genera un conflicto de fusión. Visual Studio Code cuenta con un editor de combinación integrado que resalta las versiones en disputa, permitiendo al usuario elegir entre conservar los cambios propios, los entrantes, ambos, o redactar una versión combinada manualmente.
  A su vez, esta potente herramienta destaca por su capacidad de integrar diagramas de flujo, secuencia y arquitectura directamente dentro del documento mediante el uso de sintaxis de Mermaid, PlantUML, WebSequenceDiagrams y Chart.js, eliminando la necesidad de herramientas externas o de generar imágenes por separado. Asimismo, incluye tipografía matemática compatible con KaTeX y MathJax, lo que resulta especialmente útil para la documentación técnica, científica o académica que requiere notación compleja. Su flexibilidad se extiende al ámbito de la exportación, permitiendo convertir el contenido de forma directa a PDF, HTML, PNG e imágenes, además de integrarse con Pandoc para conversiones avanzadas hacia formatos de procesador de texto.
  
  **Instalación:**
  
  1. Abrir el panel de **Extensiones** en Visual Studio Code (ícono de cuadrados en la barra lateral, o `Ctrl + Shift + X`).
  2. Buscar **"Markdown Preview Enhanced"**.
  3. Verificar que el autor sea *Yiyi Wang* (identificador `shd101wyy.markdown-preview-enhanced`), ya que existen extensiones con nombres similares desarrolladas por terceros.
  4. Hacer clic en **Instalar**.
  
  **Activación de la vista previa:**
  
  Una vez instalada, la vista previa mejorada puede abrirse mediante:
  
  - El atajo de teclado **Ctrl + K, seguido de V** (nótese que, en versiones recientes, este es el atajo correspondiente a "Markdown Preview Enhanced: Open Preview to the Side"; el atajo del visor nativo de VS Code es `Ctrl + Shift + V`, por lo que conviene no confundir ambos).
  - Haciendo clic derecho sobre el archivo `.md` abierto y seleccionando **"Open Preview to the Side"**.
  - Mediante la paleta de comandos (`Ctrl + Shift + P`), escribiendo **"Markdown Preview Enhanced: Open Preview to the Side"**.


## Referencias

- Meza, M. (2025). *Getting Started with Git and GitHub: From Zero to Teamwork*. Medium. Disponible en: https://medium.com/@moises.meza/getting-started-with-git-and-github-from-zero-to-teamwork-683c634baac8
- Chacon, S. y Straub, B. (2014). *Pro Git* (2.ª ed.). Apress. Disponible en: https://git-scm.com/book/en/v2
- Wang, Y. (shd101wyy). (s.f.). *Markdown Preview Enhanced — Documentación oficial*. Disponible en: https://shd101wyy.github.io/markdown-preview-enhanced/
