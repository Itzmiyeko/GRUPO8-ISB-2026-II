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
Es una plataforma de alejamiento en la nube que usa Git como motor subyacente, incluida en ella una serie de capas de servicios adicionales: 
- Repositorios remotos accesibles.
- Tools de gestión de proyectos, como cronogramas, tableros Kanban, milestones, etc.
- Revisión de códigos
- Integración de flujos de automatización
- Controles de accesos y permisos a repositorios.

En consecuencia, mientras que Git puede utilizarse de manera completamente independiente sin necesidad de GitHub, GitHub no podría existir sin Git, ya que depende de él para gestionar el versionado de los proyectos que aloja. Existen, además, plataformas alternativas que cumplen una función similar a GitHub, como GitLab o Bitbucket, todas ellas construidas sobre la base de Git.

## 2. Comandos principales
Los comandos fundamentales que conforman el flujo de trabajo por medio de Git para poder editar en Github:
* **git init:** inicia el rastreo de historial de edits en un repositorio, conviertiéndolo en uno local de Git.
* **git add:** agrega todos los cambios realizados al área de trabajo, es decir, selecciona que modificaciones se incluirán en el próximo registro de cambios.
* **git commit:** representa el último guardado en el repositorio local.
* **git push:** sube los cambios confirmados (commits) desde el repositorio local hacia GitHub, es decir, traslada la información de local a remoto.
* **git pull:** descarga los cambios que se encuentren en línea, ya sea porque fueron subidos desde otro equipo propio o por otros colaboradores del proyecto, e integra dichos cambios al entorno local.

## 3. Manejo desde VS Code
Visual Studio Code permite ejecutar todo este flujo de trabajo de manera visual, sin necesidad de escribir los comandos manualmente en la terminal, a través del panel de "Control de código fuente". El orden recomendado de trabajo es el siguiente:

1. Pull: antes de comenzar a trabajar, se recomienda actualizar el repositorio local descargando los cambios más recientes del repositorio remoto, evitando así conflictos posteriores.
2. Add (nueva modificación): una vez realizados los cambios en los archivos, estos se agregan al área de preparación seleccionándolos desde el panel de control de código fuente.
3. Commit con descripción: se redacta un mensaje que explique el cambio realizado y se confirma el registro, quedando guardado en el historial local del proyecto.
4. Push: Sincronización: finalmente, se sincronizan los cambios confirmados, enviándolos al repositorio remoto en GitHub para que queden disponibles en línea.

## 4. Buenas prácticas
Se recomienda un uso ordenado del flujo de trabajo descrito, se recomienda considerar:
* **Configuración inicial:**
antes de realizar cualquier modificación al repositorio remoto, es indispensable configurar la identidad del usuario en Git, mediante los siguientes comandos:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

* **Creación de un repositorio:**
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

* **Creación de ramas:**
Las ramas, también llamadas branchs, permiten que varias personas trabajen simultáneamente sobre un mismo proyecto sin interferir entre sí. Se recomienda que el líder del equipo sea quien decida qué versión final se integrará a la rama principal, evitando así tener que lidiar con conflictos de fusión (merge conflicts) causados por modificaciones simultáneas sobre las mismas líneas de código.

* **Extensión "Markdown Preview Enhanced":**
Se recomienda instalar esta extensión, ya que permite visualizar una vista previa de cómo se verá el documento renderizado antes de subirlo al repositorio. Dicha vista previa puede activarse mediante el atajo de teclado Ctrl + k, luego se sueltan ambas teclas e inmediatamente después presionar la tecla y.

Lo que podemos decir es que Visual Studio Code funciona como el intermediario visual que resume la ejecución de comandos por Git, , sin eliminar la necesidad de comprender los conceptos subyacentes, los cuales resultan muy esencial e ineludible para un uso eficaz en proyectos de mayor complejidad.
Además, cuando dos o más colaboradores modifican simultáneamente las mismas líneas de un archivo en el repositorio, Git genera un conflicto de fusión. Visual Studio Code cuenta con un editor de combinación integrado que resalta las versiones en disputa, permitiendo al usuario elegir entre conservar los cambios propios, los entrantes, ambos, o redactar una versión combinada manualmente.
