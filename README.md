# Trabajo Práctico Integrador — Organización Empresarial

**Tecnicatura Universitaria en Programación a Distancia — Universidad Tecnológica Nacional**
Alumno: Lucas Germán Caputo (trabajo individual) · Docente titular: Prof. Gabriela Martínez · Docente tutor: Prof. Guillermo Miguel Carvajal

## Caso de estudio

**LGC Advisors**, consultora argentina de seguros (Productor Asesor de Seguros), inversiones y marketing digital para pymes.
**Proyecto:** módulo de software de **gestión de clientes y cartera** (CRM) que reemplaza la planilla de cálculo por una base de datos relacional, con alertas de vencimiento, registro de consultas de WhatsApp, control de comisiones y tablero de indicadores.

**Documento integrador final:** [`entregas/TPI_Final_Caputo.pdf`](entregas/TPI_Final_Caputo.pdf) · [Tablero del proyecto (GitHub Projects)](https://github.com/users/Aiden94/projects/1)

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
- Al ser un trabajo individual, la revisión de pares se hace como **autorrevisión documentada**: en cada Pull Request dejo un comentario de revisión con lo correcto y lo que hay que ajustar, aplico la corrección con un commit en la misma rama y recién después integro a `main`.
- Detalle en [`gestion/flujo-de-trabajo.md`](gestion/flujo-de-trabajo.md).

## Declaración de Uso de IA

Usé el asistente **Claude (Anthropic)** en todas las entregas. El detalle por artefacto está en [`control/uso-de-ia.md`](control/uso-de-ia.md). Los commits hechos con su asistencia llevan la línea `Co-Authored-By: Claude`.

### Prompts utilizados y para qué

| Entrega | Qué le pedí a la IA (prompt resumido) | Por qué |
|---|---|---|
| 1 | "Ordená la estructura del documento y redactá un primer borrador a partir de cómo funciona mi consultora; proponé un diagrama de sistema abierto." | Llegar rápido a una estructura prolija y dedicar el tiempo a los datos reales. |
| 2 | "Con estas tareas y duraciones, calculá fechas, precedencias y camino crítico; graficá el FODA y el Gantt." | Evitar errores de cálculo en un cronograma de 23 tareas. |
| 3 | "Proponé un listado inicial de campos y tipos para estas entidades; dibujá el organigrama con estas áreas." | Partir de una base y ajustarla a la operación real. |
| 4 | "Modelá en BPMN 2.0 el proceso de renovación que te describo; armá el repositorio con ramas y PRs; proponé historias de usuario e indicadores a partir de las metas." | Aplicar la notación y las herramientas correctamente. |

### Correcciones humanas sobre los resultados

- **Datos y valores:** los datos de la consultora, las duraciones del Gantt (según mis 20 h semanales), los valores de las metas y los valores de las listas (ramos, canales, motivos de baja) los definí yo, no la IA.
- **Áreas y responsables:** las áreas del organigrama, la asesoría externa como staff y el responsable de cada dato salen de cómo trabajo hoy.
- **BPMN:** definí qué tareas quedan en manos del productor (las que requieren matrícula o criterio profesional) y cuáles pasan al sistema.
- **Revisión:** revisé cada Pull Request antes de integrarlo y verifiqué los conceptos contra la bibliografía de la materia.

### Criterio

La IA aceleró la redacción, los cálculos y los gráficos (estrategia DO del FODA). Las decisiones de diseño son mías y puedo justificarlas: qué proceso modelar, dónde decide una persona y dónde el sistema, la separación entre metas de proyecto y de desempeño, y el uso de `Decimal` para importes y de texto para los documentos. Asumo la responsabilidad por la veracidad y coherencia de todo lo presentado.
