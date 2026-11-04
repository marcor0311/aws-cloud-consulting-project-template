# AWS Cloud Consulting Project Template

Base para crear un repositorio independiente por proyecto aprobado de la
consultora. La estructura organiza el trabajo de las seis fases y está preparada
para trabajar con Codex mediante [AGENTS.md](AGENTS.md).

Esta copia contiene instrucciones iniciales. No representa un proyecto aprobado
ni incluye infraestructura, datos de clientes o entregables terminados.

## Crear un proyecto desde la plantilla

1. Habilitar **Template repository** en GitHub para este repositorio y crear
   cada proyecto con **Use this template**.
2. Reemplazar esta introducción por el nombre, objetivo, alcance, criterios de
   éxito y responsables del nuevo proyecto. Usar el identificador de empresa
   que entregue el backend de la consultora.
3. Incorporar el descubrimiento aprobado y la decisión ejecutiva en las áreas
   correspondientes. Las fases posteriores comienzan pendientes.
4. Configurar los responsables reales en [.github/CODEOWNERS](.github/CODEOWNERS),
   los accesos y las reglas de revisión de `main` en el nuevo repositorio.
   La configuración de protección se realiza en GitHub.
5. Crear la tarea de arquitectura con el formulario de issues, enlazar sus
   insumos y asignarla al arquitecto responsable.
6. Abrir el repositorio en Codex. Configurar en el entorno del equipo los accesos
   a GitHub, baselines y herramientas del backend que necesite la tarea.

## Organización por fase

1. [Descubrimiento y preparación](docs/01-discovery/README.md): Engagement
   Manager, requisitos, alcance e insumos de las reuniones.
2. [Priorización](docs/02-board/README.md): dirección ejecutiva, decisión de
   continuar, prioridad y presupuesto autorizado.
3. [Arquitectura](docs/03-architecture/README.md): Cloud Solutions Architect,
   diseño AWS y decisiones aprobadas.
4. [Costos](docs/04-finops/README.md): FinOps Analyst, estimación, Excel y
   validación del presupuesto.
5. [Implementación y operación](docs/05-engineering/README.md): Cloud
   Infrastructure Engineer, código en [infra/](infra/README.md), validaciones en
   [tests/](tests/README.md) y evidencias de la entrega.
6. [Informe ejecutivo y cierre](docs/06-executive/README.md): Engagement
   Manager, resultados, informe aprobado y aceptación del cierre.

Cada área comienza con una guía. Los documentos, diagramas, Excel, PDF, código y
pruebas se crean cuando se trabaja la fase correspondiente, con referencias a
los insumos y versiones que se utilizaron.

## Información y coordinación

La documentación del proyecto se centraliza en este repositorio, organizada por
fase y con historial de versiones. Cada entrega conserva su ubicación: las fases
siguientes la referencian en lugar de mantener copias divergentes.

PostgreSQL, en el backend de la consultora, mantiene empresas, ubicaciones,
contactos, correos, estado del proceso, tiempos y handoffs. El modelo detallado
de esos datos se definirá después. Este repositorio conserva las referencias
a los registros y las decisiones necesarias para entender el proyecto.

Los issues identifican fase, responsable, insumos y criterios de aceptación.
Los PRs reúnen cambios y resultados de validación. La aprobación humana queda
registrada en la herramienta correspondiente; el backend registra los handoffs
y sus referencias a issues, commits, PRs y entregables.

Los agentes usan las herramientas autorizadas del backend para actualizar el
proceso. LangGraph y PostgreSQL se operan en la plataforma de la consultora y no
se instalan en cada copia de esta plantilla.

## Baselines e implementación

Consultar `aws-cloud-consultant-baseline-modules` para seleccionar módulos.
Documentar la versión o commit aprobado de cada dependencia en arquitectura y
utilizar esa referencia en la implementación. Los cambios de módulos se revisan
en el repositorio de baselines.

El stack, los entornos y los comandos de implementación se definen a partir del
diseño aprobado. Las áreas [infra/](infra/README.md) y [tests/](tests/README.md)
explican cómo incorporarlos. Las tareas pueden documentarse en Markdown e issues
sin instalar una metodología adicional.

## Validación disponible

Desde la raíz, con Node.js y Gitleaks instalados:

```sh
npx --yes markdownlint-cli2@0.24.0 "**/*.md"
gitleaks dir . --no-banner --redact=100
git diff --check
```

Usar Gitleaks 8.30.1 para coincidir con el workflow. La ejecución local con `dir`
revisa también los archivos nuevos. En CI se revisa el historial del repositorio
y el formato de Markdown mediante [.github/workflows/checks.yml](.github/workflows/checks.yml).

Todavía no hay código de infraestructura ni pruebas de una solución. Cada
proyecto debe añadir sus validaciones cuando elija el stack, y actualizar estas
instrucciones y el workflow con los comandos reales.

## Credenciales y documentos restringidos

Configurar credenciales en el entorno de cada equipo o en el gestor de secretos
autorizado. `.gitignore` excluye archivos privados y estado local; las plantillas
de configuración que se agreguen deben carecer de valores reales.

Cuando un documento requiera almacenamiento restringido, dejar en su área la
referencia controlada y una descripción de su propósito. El repositorio mantiene
el índice documental y las versiones necesarias para cada entrega.
