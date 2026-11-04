# Instrucciones para Codex

Este repositorio es una plantilla inicial de AWS Cloud Consultant Agent.
De momento, el proceso se define en el repositorio original de la consultora.

## Trabajo en la plantilla

- Conserva las carpetas numeradas y sus `.gitkeep` mientras estén vacías.
- Añade contenido únicamente según la tarea solicitada. Las fases todavía no
  tienen guías, entregables ni reglas operativas propias en este repositorio.
- Mantén el README principal como una descripción breve del template.
- Conserva credenciales y configuración personal fuera de Git.

## Validación disponible

Desde la raíz:

```sh
npx --yes markdownlint-cli2@0.24.0 "**/*.md"
gitleaks dir . --no-banner --redact=100
git diff --check
```

Usa Gitleaks 8.30.1. El workflow comprueba Markdown y secretos del historial.
