# Progress

> Registro cronológico del avance del proyecto. La entrada más reciente va arriba.
> Cada agente (Claude, Codex, opencode, Gemini) debe leer este archivo al iniciar una sesión
> y actualizarlo al terminar un bloque de trabajo significativo.

## Índice

> Mantener sincronizado: al añadir/editar una entrada del historial, actualizar también su fila aquí.
> Para saltar a una entrada, buscar su ancla (`#` + título en minúsculas con guiones).

| Fecha | Hito | Estado | Ancla |
|---|---|---|---|
| 2026-07-19 | Descubrimiento: ingesta del brief y entrevista cerradas | completado | `#2026-07-19--descubrimiento-ingesta-del-brief-y-entrevista-cerradas` |
| 2026-07-20 | Discovery redactado y aprobado; prototipo materializado (pendiente de gate y commit) | en progreso | `#2026-07-20--discovery-redactado-y-aprobado-prototipo-materializado-pendiente-de-gate-y-commit` |

## Formato

```
### [YYYY-MM-DD] — <título breve del hito>
- **Estado:** en progreso | completado | bloqueado
- **Resumen:** qué se hizo en esta sesión.
- **Siguiente paso:** qué queda pendiente inmediatamente después.
- **Referencias:** archivos, tareas ([[tasks]]) o decisiones ([[decisions]]) relacionadas.
```

---

## Historial

### [2026-07-19] — Descubrimiento: ingesta del brief y entrevista cerradas

- **Estado:** completado

- **Resumen:**
  Primera sesión de trabajo del proyecto. La memoria estaba inicializada pero vacía y el
  directorio **no era repositorio git**; se ejecutó el bootstrap (`git init -b main`) con
  autorización del humano. No se tocó el remoto (compete al cierre de sesión).

  Se completaron las **dos primeras etapas del estadio de Prototipo**:

  1. **Ingesta** (`onboarding-reader` / `ingest-protocol`) → `_prototype/document_extract.md`,
     con citas del brief mapeadas a §1–§10 y tabla de cobertura. Confirmado por el humano.
     Commits `087d2f3` (borrador) y `13d42d5` (aprobado).
  2. **Entrevista** (`onboarding-interviewer` / `interview-protocol`) →
     `_prototype/interview_document.md`, **cerrada** con 12 entradas (11 de contenido + cierre).
     Checkpoints intra-etapa `df72692`, `f07708b`, `33807ed`, `239a512`, `19be3bf`;
     cierre en `93ab5e5`.

  El humano fijó timebox de 20–25 preguntas y priorizó el flujo del cliente y del Analista de
  Operaciones. Bastaron **11 preguntas**: todas las áreas §1–§10 quedaron resueltas (cubiertas,
  `n/a` o hueco declarado) y las **tres ambigüedades A1–A3** del brief se cerraron con decisiones
  propias del cliente. Ver [[decisions]] D-001…D-007.

  **Huecos declarados conscientemente** (no son omisiones): dashboards gerenciales (sacrificables,
  con datos de muestra) y el contenido real de la tabla camión × material × tamaño, comprometido
  por el humano para el **día hábil 3** del prototipado (ver [[assumptions]] A-001).

  **Incidente de proceso:** `document_extract.md` resultó incompleto — perdió la convención de
  colores que sí estaba en el brief (líneas 56 y 58). Se detectó porque el humano lo señaló al
  recibir una pregunta redundante. Ver [[lessons]] L-001.

- **Siguiente paso:**
  Redactar `_prototype/discovery.md` con el `onboarding-writer` (skill `discovery-protocol`),
  contrastando **también contra `_context/client_brief.md`** y no solo contra el extracto y el log.
  Antes, queda pendiente la decisión del humano sobre T-002 (auditar brief vs. extracto).

- **Referencias:**
  `_prototype/document_extract.md`, `_prototype/interview_document.md`, `_context/client_brief.md`,
  [[tasks]] T-001…T-007, [[decisions]] D-001…D-007, [[constrains]] C-001…C-004,
  [[assumptions]] A-001…A-003, [[lessons]] L-001, L-002.

### [2026-07-20] — Discovery redactado y aprobado; prototipo materializado (pendiente de gate y commit)

- **Estado:** en progreso

- **Resumen:**
  1. **T-001 completada.** El `onboarding-writer` (skill `discovery-protocol`) sintetizó
     `interview_document.md` + `document_extract.md` + `_context/client_brief.md` original en
     `_prototype/discovery.md`. Aplicó L-001: recuperó del brief original la convención de colores
     que la ingesta había perdido, y documentó el incidente dentro del propio entregable. Resolvió
     A2 a favor de la entrevista (ver D-001, ratificada). Fijó el gatekeeper conjuntivo de D-007,
     explícitamente distinto del 60% adopción / NPS>85% del proyecto a 6 meses. Declaró huecos
     conscientes: dashboards gerenciales, contenido real de la rejilla camión × material × tamaño,
     flujo del Conductor no elicitado en profundidad. **Aprobado por el humano**, discovery marcado
     "cerrado". Commit `405c8fb`.
  2. **T-006 materializada, pendiente de gate.** El `prototype-builder` construyó
     `_prototype/prototype/` (Node.js puro, sin dependencias, `node server.js`, puerto 4000; cliente
     en `/`, operador en `/operador/`). Motor de asignación real, datos precargados, credenciales
     demo documentadas en su README. El agente hizo un commit propio y luego se ejecutó
     `git reset HEAD~1` por instrucción del humano; se verificó que el historial (`405c8fb` como
     HEAD) quedó intacto. **`_prototype/prototype/` sigue SIN COMMIT** (untracked) al cierre de
     esta sesión — decisión deliberada, no pendiente por descuido.
  3. **Verificación propia del prototipo (humano + agente, no el reporte del `prototype-builder`).**
     Se levantó el servidor y se ejercitó por API. Criterio 2 del gatekeeper CUMPLE con las 3
     solicitudes precargadas. Se detectaron **dos hallazgos no reportados por el agente
     constructor**: (a) a la cuarta solicitud del mismo tipo de camión en la misma franja el motor
     devuelve `SIN_UNIDAD_DISPONIBLE_HUECO`, lo que violaría la regla dura 3 de D-002 — con 3
     solicitudes cumple, pero el margen es cero; (b) de tres solicitudes del mismo tipo, solo la
     primera se asigna dentro de su zona, las otras dos salen con `zonaAmpliada=true` — el motor
     sacrifica la regla de zona para salvar la de "nunca sin asignar", decisión **no declarada** en
     el discovery. Ver [[lessons]] L-004.
  4. **Desviaciones del prototipo respecto al discovery, declaradas por el propio agente
     constructor:** correo real (D-004) quedó **simulado** (log interno `/api/emails`, contenido
     correcto, marcado `simulado: true`) por exigir credenciales SMTP externas; se añadió un botón
     "⏩ demo: adelantar reloj" en el panel del operador (herramienta de demo, no producto); la
     precarga se amplió a 3 unidades por tipo de camión tras detectar el límite de capacidad del
     punto 3.
  5. **T-005 se manifestó en vivo:** el `onboarding-writer` no pudo hacer su propio commit por
     carecer de `Bash`; lo ejecutó el orquestador. Confirma que la tarea sigue vigente (ver L-002).

- **Siguiente paso:**
  Decidir sobre las tres cosas abiertas del prototipo antes de darlo por materializado para el
  gatekeeper: (a) ampliar el límite de capacidad de unidades (el tope de 4 es un riesgo delante
  del comité, ver T-010); (b) aceptar o corregir las desviaciones correo-simulado y
  `zonaAmpliada` (T-011); (c) una vez resuelto lo anterior, confirmar `_prototype/prototype/` en
  un commit propio (T-012). En paralelo siguen abiertas T-003 (tabla real, día hábil 3, reloj
  corriendo), T-004 (agendar Analista de Operaciones en frío) y T-005 (agentes sin `Bash`).
  T-002 quedó de facto superada porque el writer sí contrastó contra el brief original al
  redactar el discovery; se deja a criterio de la próxima sesión cerrarla o replantearla.

- **Referencias:**
  `_prototype/discovery.md`, `_prototype/prototype/` (sin commit), [[tasks]] T-001, T-002, T-006,
  T-010, T-011, T-012, [[decisions]] D-001, D-002, D-004, D-007, [[lessons]] L-004.
