# Flujo de trabajo con Git y GitHub

## Ramas

| Rama | Uso |
|---|---|
| `main` | Versión revisada. No se trabaja directamente sobre ella. |
| `docs/<tema>` | Documentación (entregas, historias, indicadores). |
| `feature/<artefacto>` | Artefactos del sistema (organigrama, diccionario de datos, BPMN). |

## Ciclo de cada cambio

1. Se toma un issue del tablero y se pasa a **En curso**.
2. Se crea una rama desde `main`: `git switch -c feature/bpmn-renovacion`.
3. Se hacen commits pequeños con mensaje descriptivo: `feat(bpmn): agrega compuerta basada en eventos para la respuesta del cliente`.
4. Se abre un **Pull Request** hacia `main` con descripción y `Closes #n` para vincular el issue.
5. Se revisa el PR (coherencia con las entregas anteriores) y se fusiona. El issue se cierra solo y la tarjeta pasa a **Hecho**.

## Convención de commits

`tipo(alcance): descripción en minúscula y en presente`

- `docs`: documentación · `feat`: nuevo artefacto o funcionalidad · `fix`: corrección · `chore`: mantenimiento
