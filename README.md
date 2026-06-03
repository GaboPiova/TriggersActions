# Trabajo Práctico: Automatización con Triggers en GitHub Actions

**Estudiante:** Gabriel Piovano (Gabo)  
**Especialidad:** Administración de Servidores  

## Descripción del Proyecto
Este repositorio contiene la configuración y demostración de 6 workflows automatizados en GitHub Actions, configurados para responder a diferentes eventos (*triggers*) del ciclo de vida del desarrollo. Además, se implementó un sistema de auditoría interna automatizado que registra cada evento en un archivo `eventos.log`.

---

## Detalle de los 6 Workflows y sus Triggers

### 1. Workflow con push (`on: push`)
* **Qué hace:** Se dispara automáticamente de forma síncrona cada vez que se empuja código nuevo o se hace un merge directo a la rama principal (`main`).
* **Evidencia:** * *[Insertar Captura de Pantalla del log del workflow imprimiendo "Workflow activado por push"]*

### 2. Workflow con pull_request (`on: pull_request`)
* **Qué hace:** Se activa en el momento que un desarrollador abre una propuesta de cambio (Pull Request) hacia la rama `main`, permitiendo validar cambios antes de fusionarlos.
* **Evidencia:** * *[Insertar Captura de Pantalla abriendo un PR y el check ejecutándose]*

### 3. Workflow con issues (`on: issues`)
* **Qué hace:** Responde a eventos relacionados con los Issues del repositorio. Está configurado con el tipo `opened` para reaccionar inmediatamente cuando se reporta un nuevo bug o tarea.
* **Evidencia:** * *[Insertar Captura de Pantalla creando un Issue de prueba]*

### 4. Workflow con issue_comment (`on: issue_comment`)
* **Qué hace:** Detecta comentarios. GitHub unifica los comentarios de Issues y Pull Requests bajo este trigger, por lo que se le aplicó un filtro condicional (`if`) para que se ejecute estrictamente si el comentario pertenece a un Pull Request.
* **Evidencia:** * *[Insertar Captura de Pantalla comentando adentro de un PR]*

### 5. Workflow con workflow_dispatch (`on: workflow_dispatch`)
* **Qué hace:** Permite la ejecución manual del workflow desde la interfaz web de GitHub Actions. Incluye un menú interactivo (`choice`) que obliga al operador a seleccionar el nivel de criticidad (INFO, WARNING, CRITICAL) antes de iniciar.
* **Evidencia:** * *[Insertar Captura de Pantalla del menú desplegable y del output mostrando el valor elegido]*

### 6. Workflow con schedule (`on: schedule`)
* **Qué hace:** Ejecución basada en tiempo utilizando la sintaxis estándar de `cron`. Está configurado para dispararse de manera asíncrona cada hora exacta (`0 * * * *`) para tareas de mantenimiento repetitivas.
* **Evidencia:** * *[Insertar Captura de Pantalla de la ejecución en el historial de Actions]*

---

## Evidencia del Archivo de Logs Automatizado
Como característica de valor agregado, cada flujo de trabajo tiene un paso final que actualiza de manera persistente el archivo `eventos.log` reflejando el historial del repositorio:

```text
[Ejemplo del contenido de tu archivo eventos.log]
[2026-06-03 12:00:00] TRIGGER: push - Workflow activado por push en main.
[2026-06-03 12:05:22] TRIGGER: workflow_dispatch - Ejecución manual. Nivel: CRITICAL.