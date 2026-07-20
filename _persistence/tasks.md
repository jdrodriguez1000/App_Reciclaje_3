# Tasks

> Lista viva de tareas del proyecto. Fuente única de trabajo pendiente y en curso.
> Estados: `[ ]` pendiente · `[~]` en progreso · `[x]` completada · `[!]` bloqueada.

## Índice

> Mantener sincronizado: al crear/mover/cerrar una tarea, actualizar su fila aquí.
> Buscar por ID (`T-XXX`) para localizar la tarea sin leer todo el archivo.

| ID | Tarea | Estado | Prioridad |
|---|---|---|---|
| T-001 | Redactar `discovery.md` con el `onboarding-writer` | completada | alta |
| T-002 | Auditar `client_brief.md` contra `document_extract.md` | bloqueada | alta |
| T-003 | Conseguir la tabla real camión × material × tamaño (día hábil 3) | pendiente | alta |
| T-004 | Agendar la sesión del Analista de Operaciones en frío | pendiente | alta |
| T-005 | Corregir definiciones de agentes sin `Bash` | pendiente | media |
| T-006 | Materializar el prototipo con el `prototype-builder` | en progreso | media |
| T-007 | Separar la sesión del analista de la demo del comité | pendiente | media |
| T-008 | Ingesta del documento del cliente | completada | alta |
| T-009 | Entrevista de descubrimiento | completada | alta |
| T-010 | Ampliar capacidad de unidades por tipo de camión (riesgo de demo) | pendiente | alta |
| T-011 | Decidir sobre desviaciones correo-simulado y `zonaAmpliada` | pendiente | alta |
| T-012 | Confirmar `_prototype/prototype/` en un commit | pendiente | alta |

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

- [ ] T-007 — Separar la sesión del analista en frío (T-004) de la demo del comité.
      Prioridad: media · Responsable: humano (Analista de Negocios) · Ref: [[decisions]] D-007
      Los criterios 1 y 3 del gatekeeper empujan en direcciones opuestas: el 1 pide una demo en
      vivo sin tropiezos, el 3 pide un usuario no entrenado tocando la pantalla. Juntarlos en la
      misma reunión obliga a sacrificar uno de los dos.

- [ ] T-010 — Ampliar la capacidad de unidades por tipo de camión en los datos de demo.
      Prioridad: alta · Responsable: `prototype-builder` / humano · Ref: [[progress]], [[lessons]] L-004
      Hallazgo de verificación: con el límite actual (3 unidades por tipo, precargadas), la cuarta
      solicitud del mismo tipo de camión en la misma franja cae en `SIN_UNIDAD_DISPONIBLE_HUECO`,
      lo que violaría la regla dura 3 de D-002 si ocurriera delante del comité. El margen frente al
      criterio 2 del gatekeeper (3 solicitudes) es hoy cero.

- [ ] T-011 — Decidir sobre las desviaciones del prototipo frente al discovery aprobado.
      Prioridad: alta · Responsable: humano (Analista de Negocios) · Ref: [[progress]], [[decisions]] D-004, D-002
      Dos desviaciones declaradas por el `prototype-builder` no estaban en `discovery.md`: (a) el
      correo real de D-004 quedó simulado (marcado `simulado: true`, motivo: credenciales SMTP
      externas); (b) el motor asigna con `zonaAmpliada=true` a la segunda y tercera solicitud del
      mismo tipo de camión, sacrificando la afinidad de zona para no dejar nada sin asignar. Para
      cada una: o se aceptan y se anotan explícitamente en `discovery.md`, o se corrigen antes del
      gate.

- [ ] T-012 — Confirmar `_prototype/prototype/` en un commit.
      Prioridad: alta · Responsable: humano / agente · Ref: [[progress]]
      Depende de resolver T-010 y T-011 primero: el directorio quedó deliberadamente sin commit al
      cierre de esta sesión para no fijar en el historial un estado con riesgos sin decidir.

## En progreso

- [~] T-006 — Materializar el prototipo desechable del camino feliz.
      Prioridad: media · Responsable: `prototype-builder` · Ref: [[decisions]] D-001…D-007, [[progress]]
      Dependía de T-001 (discovery cerrado, ya completada). El prototipo está construido y
      funcional en `_prototype/prototype/`, pero pendiente de gate: ver T-010, T-011, T-012.

## Completadas

- [x] T-001 — Redactar `_prototype/discovery.md` a partir de `interview_document.md`,
      `document_extract.md` y `_context/client_brief.md` original. Aprobado por el humano, estado
      "cerrado". Ref: [[progress]] · Commit `405c8fb`

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
