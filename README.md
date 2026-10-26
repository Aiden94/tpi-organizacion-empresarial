# Trabajo Práctico Integrador — Organización Empresarial

**Tecnicatura Universitaria en Programación a Distancia — Universidad Tecnológica Nacional**
Alumno: Lucas Germán Caputo (trabajo individual) · Docente titular: Prof. Gabriela Martínez · Docente tutor: Prof. Guillermo Miguel Carvajal

## Caso de estudio

**LGC Advisors**, consultora argentina de seguros (Productor Asesor de Seguros), inversiones y marketing digital para pymes.
**Proyecto:** módulo de software de **gestión de clientes y cartera** (CRM) que reemplaza la planilla de cálculo por una base de datos relacional, con alertas de vencimiento, registro de consultas de WhatsApp, control de comisiones y tablero de indicadores.

Tablero del proyecto: GitHub Projects (enlace en la pestaña Projects)

## Contenido del repositorio

| Carpeta | Contenido | Entrega |
|---|---|---|
| [`entregas/`](entregas) | PDF de cada entrega y documento integrador final | 1 a 4 |
| [`diagramas/organigrama/`](diagramas/organigrama) | Organigrama piramidal vertical | 3 |
| [`datos/`](datos) | Diccionario de datos inicial del CRM | 3 |
| [`diagramas/bpmn/`](diagramas/bpmn) | Proceso de renovación de pólizas en BPMN 2.0 (`.bpmn`, `.svg`, `.png`) | 4 |
| [`gestion/`](gestion) | Historias de usuario y forma de trabajo con ramas y Pull Requests | 4 |
| [`control/`](control) | Indicadores de control y declaración de uso de IA | 4 |

## Recorrido del TPI

1. **Entrega 1 — La organización y su enfoque sistémico:** LGC Advisors como sistema abierto y propuesta del módulo CRM.
2. **Entrega 2 — Diagnóstico y planeación:** FODA, objetivo general, metas M1 a M6 y Diagrama de Gantt (oct. 2026 a feb. 2027).
3. **Entrega 3 — Estructura formal y diseño de datos:** organigrama y diccionario de datos (7 entidades).
4. **Entrega 4 — Cierre:** BPMN, gestión con Git y GitHub, tablero ágil, indicadores de control y uso de IA.

## Forma de trabajo

- `main` contiene solo trabajo revisado. Cada artefacto se desarrolla en una rama propia (`docs/...`, `feature/...`) y se integra mediante **Pull Request**.
- Los commits siguen la convención `tipo(alcance): descripción` en español (`docs`, `feat`, `fix`).
- Las tareas se gestionan como **issues** en el tablero; los hitos del Gantt son **milestones** (H1 a H4).
- Detalle en [`gestion/flujo-de-trabajo.md`](gestion/flujo-de-trabajo.md).

## Uso de inteligencia artificial

Se usó el asistente Claude (Anthropic) con fines declarados en [`control/uso-de-ia.md`](control/uso-de-ia.md). Los commits generados con su asistencia llevan la línea `Co-Authored-By: Claude`.
