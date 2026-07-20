# Assumptions

> Supuestos que se dan por ciertos pero NO están confirmados.
> Si un supuesto se confirma → se promueve a [[decisions]] o [[constrains]].
> Si se refuta → se documenta la corrección en [[lessons]].

## Índice

> Mantener sincronizado: al registrar o cambiar el estado de un supuesto, actualizar su fila aquí.
> Buscar por ID (`A-XXX`) para localizar el supuesto sin leer todo el archivo.

| ID | Supuesto | Estado | Fecha |
|---|---|---|---|
| A-001 | La tabla provisional camión × material × tamaño sirve hasta el día 3 | sin validar | 2026-07-19 |
| A-002 | Habrá un Analista de Operaciones disponible para la prueba en frío | sin validar | 2026-07-19 |
| A-003 | El extracto de la ingesta puede tener más omisiones no detectadas | sin validar | 2026-07-19 |

## Formato

```
### A-001 — <supuesto>
- **Estado:** sin validar | confirmado | refutado
- **Impacto si es falso:** qué se rompe o cambia si el supuesto no se cumple.
- **Cómo validarlo:** acción para confirmar o descartar.
- **Fecha:** YYYY-MM-DD
```

---

## Supuestos

### A-001 — La tabla provisional camión × material × tamaño sirve hasta el día hábil 3

- **Estado:** sin validar
- **Impacto si es falso:** el prototipo llegaría a la demo con una clasificación de vehículos que el
  equipo de recolección no reconoce como suya. El humano lo señaló explícitamente: el equipo diría
  "eso no es así" y se perdería el **criterio 4 del gatekeeper** (compromiso verbal del Gerente de
  Operaciones, ver D-007). Si además la tabla provisional sobrevive por olvido más allá del día 8,
  el riesgo se materializa sin que nadie lo note.
- **Cómo validarlo:** T-003 — el Analista de Negocios trae del Gerente de Operaciones el contenido
  real de las 9 celdas al **día hábil 3**. Si no llega, el constructor avisa y el humano escala.
  Regla declarada: no puede llegar el día hábil 8 con la provisional puesta.
- **Nota:** solo el **contenido** está sin validar. La **estructura** (rejilla 3 × 3) sí está
  confirmada por el humano — ver D-005.
- **Fecha:** 2026-07-19

### A-002 — Habrá un Analista de Operaciones disponible para la prueba en frío

- **Estado:** sin validar
- **Impacto si es falso:** el criterio 3 del gatekeeper (D-007) —el de mayor peso declarado— no se
  podría evaluar, y como los cuatro criterios son conjuntivos, el prototipo no podría darse por
  aprobado aunque el software funcione perfecto. Es el único criterio que **no depende de construir
  bien sino de agendar**: puede fallar por pura logística.
- **Cómo validarlo:** T-004 — agendar la sesión con antelación y confirmar que la persona **no ha
  visto nada del prototipo** antes (la prueba exige que llegue en frío, sin entrenamiento previo).
  Debe ocurrir con días de margen antes del comité, no el mismo día (T-007).
- **Fecha:** 2026-07-19

### A-003 — El extracto de la ingesta puede tener más omisiones no detectadas

- **Estado:** sin validar
- **Impacto si es falso** (es decir, si hay más omisiones): el `discovery.md` heredaría vacíos que
  vienen del brief original y que nadie notó, y esos vacíos llegarían al `prototype-builder` como
  material inexistente. Se sabe con certeza que el extracto perdió la convención de colores
  (ver L-001); no se sabe si perdió algo más.
- **Cómo validarlo:** T-002 — auditar `_context/client_brief.md` completo contra
  `_prototype/document_extract.md`. **Pendiente de decisión del humano**, propuesta dos veces
  durante la sesión y sin respuesta al cierre.
- **Mitigación parcial ya aplicada:** T-001 lleva instrucción explícita de que el `onboarding-writer`
  contraste contra el brief original y no solo contra el extracto y el log.
- **Fecha:** 2026-07-19
