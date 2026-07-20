# Tasks

> Lista viva de tareas del proyecto. Fuente única de trabajo pendiente y en curso.
> Estados: `[ ]` pendiente · `[~]` en progreso · `[x]` completada · `[!]` bloqueada.

## Índice

> Mantener sincronizado: al crear/mover/cerrar una tarea, actualizar su fila aquí.
> Buscar por ID (`T-XXX`) para localizar la tarea sin leer todo el archivo.

| ID | Tarea | Estado | Prioridad |
|---|---|---|---|
| T-001 | Redactar `discovery.md` con el `onboarding-writer` | pendiente | alta |
| T-002 | Auditar `client_brief.md` contra `document_extract.md` | bloqueada | alta |
| T-003 | Conseguir la tabla real camión × material × tamaño (día hábil 3) | pendiente | alta |
| T-004 | Agendar la sesión del Analista de Operaciones en frío | pendiente | alta |
| T-005 | Corregir definiciones de agentes sin `Bash` | pendiente | media |
| T-006 | Materializar el prototipo con el `prototype-builder` | pendiente | media |
| T-007 | Separar la sesión del analista de la demo del comité | pendiente | media |
| T-008 | Ingesta del documento del cliente | completada | alta |
| T-009 | Entrevista de descubrimiento | completada | alta |

## Convención de ID

- Cada tarea tiene un ID estable: `T-001`, `T-002`, ...
- No reutilizar IDs de tareas eliminadas.
- Las subtareas se anidan bajo su tarea padre.

## Formato

```
- [ ] T-001 — <descripción de la tarea>
      Prioridad: alta | media | baja · Responsable: <agente/persona> · Ref: [[progress]]
```

---

## Backlog

- [ ] T-001 — Redactar `_prototype/discovery.md` a partir de `interview_document.md` y
      `document_extract.md`, **contrastando también contra `_context/client_brief.md`**
      (el extracto demostró estar incompleto, ver [[lessons]] L-001).
      Prioridad: alta · Responsable: `onboarding-writer` · Ref: [[progress]]
      Es el siguiente paso inmediato del proyecto y el único insumo del Prototipador.

- [ ] T-003 — Conseguir del Gerente de Operaciones el contenido real de la rejilla
      camión × material × tamaño (9 celdas: cartón/vidrio/otro × 3 tamaños) y reemplazar la
      tabla provisional. **Compromiso del humano: día hábil 3** del prototipado.
      Prioridad: alta · Responsable: humano (Analista de Negocios) · Ref: [[assumptions]] A-001
      Regla declarada: no puede llegar el día hábil 8 con la tabla provisional todavía puesta.
      Si el día 3 no llega, el constructor avisa y el humano escala.

- [ ] T-004 — Agendar a un Analista de Operaciones real para operar el prototipo **en frío**,
      sin entrenamiento previo y sin haber visto nada antes.
      Prioridad: alta · Responsable: humano (Analista de Negocios) · Ref: [[decisions]] D-007
      Es el criterio 3 del gatekeeper y el de mayor peso declarado, pero **no depende de construir
      bien sino de agendar**: es el único criterio que puede fallar por logística. Debe ocurrir
      con días de margen antes del comité, no el mismo día.

- [ ] T-005 — Corregir las definiciones de `onboarding-reader` y `onboarding-interviewer`:
      sus skills (`ingest-protocol`, `interview-protocol`) les exigen ejecutar commits, pero su
      frontmatter no incluye la herramienta `Bash`.
      Prioridad: media · Responsable: agente · Ref: [[lessons]] L-002
      Durante esta sesión el orquestador cubrió el hueco ejecutando los commits manualmente.

- [ ] T-006 — Materializar el prototipo desechable del camino feliz.
      Prioridad: media · Responsable: `prototype-builder` · Ref: [[decisions]] D-001…D-007
      Depende de T-001 (discovery cerrado). Hereda T-003 como dependencia dura con fecha.

- [ ] T-007 — Separar la sesión del analista en frío (T-004) de la demo del comité.
      Prioridad: media · Responsable: humano (Analista de Negocios) · Ref: [[decisions]] D-007
      Los criterios 1 y 3 del gatekeeper empujan en direcciones opuestas: el 1 pide una demo en
      vivo sin tropiezos, el 3 pide un usuario no entrenado tocando la pantalla. Juntarlos en la
      misma reunión obliga a sacrificar uno de los dos.

## En progreso

## Completadas

- [x] T-008 — Ingesta del documento del cliente → `_prototype/document_extract.md`, confirmado.
      Ref: [[progress]] · Commits `087d2f3`, `13d42d5`

- [x] T-009 — Entrevista de descubrimiento → `_prototype/interview_document.md`, cerrada con
      12 entradas. Ref: [[progress]] · Commit `93ab5e5`

## Bloqueadas

- [!] T-002 — Auditar `_context/client_brief.md` completo contra `_prototype/document_extract.md`
      para detectar qué más perdió la ingesta además de la convención de colores.
      Prioridad: alta · Responsable: agente · Ref: [[lessons]] L-001, [[assumptions]] A-003
      **Bloqueada por decisión del humano:** se le propuso dos veces y quedó sin responder al
      cerrar la sesión. No se ejecutó por cuenta propia porque implica revisar un artefacto que
      el humano ya confirmó como cerrado. Retomar la pregunta al inicio de la próxima sesión.
      Si se decide no hacerla, el riesgo está mitigado en parte: T-001 ya lleva instrucción de
      contrastar contra el brief original.
