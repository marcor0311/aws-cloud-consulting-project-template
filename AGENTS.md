# Instrucciones del proyecto

Este repositorio organiza un proyecto AWS de la consultora. Comienza como una
plantilla: no contiene una solución implementada ni aprobaciones reales.

## Contexto y trabajo

- Usa el README principal para localizar las seis fases numeradas y sus guías.
- Parte del issue asignado, sus criterios de aceptación y los insumos aprobados.
  Lee el contexto del área que afecta la tarea y registra las dudas pendientes.
- Conserva cada entregable en su fase. Las etapas siguientes deben referenciarlo
  para evitar copias divergentes de arquitectura, costos o decisiones.
- Documenta los cambios y sus referencias en el issue y en el PR correspondiente.
  No atribuyas al proyecto resultados, aprobaciones o despliegues inexistentes.

## Implementación y coordinación

- Consulta `aws-cloud-consultant-baseline-modules` para reutilizar módulos con
  versión o commit aprobado. Los cambios de baselines se trabajan en ese repo.
- Añade código, pruebas, scripts y configuración según el diseño aprobado.
  Mantén instrucciones de ejecución y validación junto a los cambios.
- Usa las herramientas autorizadas del backend para actualizar estado, tiempos
  y handoffs. PostgreSQL y LangGraph pertenecen a la plataforma de la consultora.
- Las personas responsables validan sus entregas. El arquitecto aprueba los PRs
  técnicos; Codex prepara cambios, evidencia y solicitudes de revisión.
- Las conexiones MCP y los accesos se configuran en el entorno del equipo.
  Mantén credenciales y datos maestros de empresa fuera del repositorio.

## Validación disponible

Desde la raíz:

```sh
npx --yes markdownlint-cli2@0.24.0 "**/*.md"
gitleaks dir . --no-banner --redact=100
git diff --check
```

Usa Gitleaks 8.30.1. El workflow valida Markdown y secretos del historial.
Cuando se incorpore una solución, documenta sus comandos reales en `infra/`,
`tests/` y esta guía, y añádelos al workflow. Informa los resultados
obtenidos y las validaciones que no pudieron ejecutarse.
