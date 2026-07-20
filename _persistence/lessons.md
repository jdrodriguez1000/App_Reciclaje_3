# Lessons Learned

> Conocimiento acumulado: errores cometidos, cómo se resolvieron y qué hacer distinto.
> Objetivo: que ningún agente repita un error ya resuelto en una sesión anterior.

## Índice

> Mantener sincronizado: al registrar una lección, añadir su fila aquí.
> Buscar por ID (`L-XXX`) para localizar la lección sin leer todo el archivo.

| ID | Lección | Fecha |
|---|---|---|
| L-001 | El extracto de la ingesta perdió contenido del brief | 2026-07-19 |
| L-002 | Dos agentes carecen de `Bash` pese a que sus skills exigen commitear | 2026-07-19 |
| L-003 | El humano corrige mejor que el agente cuando se le muestra una propuesta concreta | 2026-07-19 |

## Formato

```
### L-001 — <título de la lección>
- **Contexto:** qué se estaba haciendo.
- **Problema:** qué salió mal o qué no era obvio.
- **Solución / aprendizaje:** qué funcionó y por qué.
- **Cómo aplicarlo:** regla accionable para el futuro.
- **Fecha:** YYYY-MM-DD
```

---

## Lecciones

### L-001 — El extracto de la ingesta perdió contenido del brief

- **Contexto:** Etapa de entrevista. El `onboarding-interviewer` preguntó por la convención de
  colores del seguimiento, que el extracto marcaba como no detallada.
- **Problema:** la convención **estaba completa en el brief** (`_context/client_brief.md`,
  líneas 56 y 58) y `document_extract.md` no la capturó — se verificó buscando "colores" y
  "amarillo" en el extracto: cero coincidencias. El entrevistador trabaja sobre el extracto, no
  sobre el brief, así que para él ese dato no existía. Gastó una pregunta del presupuesto limitado
  del humano en algo ya respondido, y fue **el humano quien lo detectó**, no el harness.
- **Solución / aprendizaje:** el fallo no fue del entrevistador sino de la **etapa anterior**. Un
  artefacto intermedio confirmado por el humano no garantiza que sea completo: la confirmación
  cubre lo que está, no lo que falta. Un extracto con pérdidas silenciosas contamina toda la cadena
  aguas abajo (entrevista → discovery → prototipo) sin que ninguna etapa lo note.
- **Cómo aplicarlo:**
  1. Las etapas que consumen un artefacto derivado (`interview`, `discovery`) deben **contrastar
     también contra la fuente original** (`client_brief.md`), no fiarse solo del derivado.
  2. El `ingest-protocol` debería verificar cobertura de forma exhaustiva antes de cerrar: barrer el
     documento por secciones y confirmar que cada afirmación concreta quedó citada o descartada
     conscientemente.
  3. Cuando el humano señale que algo "ya está escrito", **verificarlo contra el archivo antes de
     responder** — ni aceptarlo ni negarlo de memoria.
- **Fecha:** 2026-07-19

### L-002 — Dos agentes carecen de `Bash` pese a que sus skills exigen commitear

- **Contexto:** Etapas de ingesta y entrevista. Ambos skills (`ingest-protocol`, `interview-protocol`)
  exigen commit de etapa y checkpoints intra-etapa según `_guideline/git-protocol.md` §3 y §3.1.
- **Problema:** las definiciones de `onboarding-reader` y `onboarding-interviewer` declaran las
  herramientas `Read, Write, Edit, Glob, Grep, Skill` — **sin `Bash`**. Los agentes no pueden
  ejecutar `git add` ni `git commit`, así que la instrucción de su propio skill es inejecutable.
  El `onboarding-reader` lo reportó honestamente en vez de fallar en silencio.
- **Solución / aprendizaje:** el orquestador cubrió el hueco ejecutando todos los commits
  manualmente. Funcionó, pero solo porque el agente **avisó**; un agente que hubiera dado el commit
  por hecho habría dejado la cadena sin puntos de retorno y nadie se habría enterado.
- **Cómo aplicarlo:**
  1. Corregir las definiciones (T-005): o se añade `Bash` a esos agentes, o el skill delega
     explícitamente el commit al orquestador en vez de instruir algo que el agente no puede hacer.
  2. Regla general: **una definición de agente y el skill que invoca deben ser coherentes en
     herramientas.** Si un skill exige una capacidad, el agente que lo ejecuta debe tenerla.
  3. Mientras no se corrija, el orquestador ejecuta los commits de esas dos etapas.
- **Fecha:** 2026-07-19

### L-003 — El humano corrige mejor que el agente cuando se le muestra una propuesta concreta

- **Contexto:** Entrevista de descubrimiento. Varias preguntas ofrecieron opciones concretas
  (a/b, esquemas de clasificación, alternativas de implementación) en vez de preguntas abiertas.
- **Problema / observación:** en al menos tres ocasiones el humano **rechazó todas las opciones
  ofrecidas y formuló una mejor**: el registro con botones inertes (D-003), la rejilla material ×
  tamaño frente al esquema de letras solapadas (D-005), y el correo real frente a la bandeja
  simulada (D-004). En el caso de D-005 detectó un defecto lógico real en la propuesta del agente.
- **Solución / aprendizaje:** proponer algo concreto y posiblemente equivocado resultó más
  productivo que preguntar en abstracto. La propuesta le da al humano algo con qué chocar, y la
  corrección trae el razonamiento — que es lo valioso. Preguntar "¿cómo debería asignarse el camión?"
  habría producido una respuesta más pobre que ofrecer un esquema con un defecto que él pudiera ver.
- **Cómo aplicarlo:**
  1. En entrevistas de descubrimiento, preferir **propuestas concretas y falsables** a preguntas
     abiertas, dejando siempre la salida "o dígalo distinto".
  2. **Registrar la corrección como decisión del humano, no del agente.** Él lo pidió
     explícitamente en D-002, y la atribución importa para que el discovery refleje quién decidió qué.
  3. No suavizar en el log las refutaciones del humano a las propuestas del agente: el razonamiento
     de por qué algo estaba mal es material de diseño reutilizable.
- **Fecha:** 2026-07-19
