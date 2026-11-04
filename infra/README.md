# Infraestructura

**Responsable:** Cloud Infrastructure Engineer, con revisión del arquitecto.

Esta área comienza sin recursos implementados. Su contenido se define a partir
del diseño aprobado en [arquitectura](../docs/03-architecture/README.md).

## Al implementar

- Añadir Terraform y organización por entornos cuando el diseño los requiera.
- Consumir los baselines mediante versiones o commits aprobados y documentados.
- Documentar herramientas, versiones, configuración y comandos reales en
  [ingeniería](../docs/05-engineering/README.md).
- Definir el almacenamiento de estado antes de desplegar. El estado de Terraform
  y los valores privados permanecen fuera de Git.
- Conservar los locks de dependencias generados por las herramientas elegidas.

Si la solución requiere código de aplicación o scripts, añadir sus áreas según
el alcance. Esta plantilla no presupone servicios, cuentas AWS ni entornos.
