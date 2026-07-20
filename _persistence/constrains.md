# Constraints

> Restricciones firmes que acotan el proyecto: técnicas, de negocio, legales, de tiempo o de recursos.
> A diferencia de [[assumptions]], una restricción NO es negociable dentro del alcance actual.
> A diferencia de [[decisions]], no es una elección nuestra: es una condición impuesta.

## Índice

> Mantener sincronizado: al registrar una restricción, añadir su fila aquí.
> Buscar por ID (`C-XXX`) para localizar la restricción sin leer todo el archivo.

| ID | Restricción | Tipo | Fecha |
|---|---|---|---|
| C-001 | Timebox del prototipo: 15 días hábiles, freeze al día 10 | tiempo | 2026-07-19 |
| C-002 | Presupuesto 45K USD y plazo de 6 meses del proyecto | recursos | 2026-07-19 |
| C-003 | Contraparte única: Analista de Negocios, con SLA de 4 horas | negocio | 2026-07-19 |
| C-004 | Exclusiones del prototipo declaradas por el cliente | negocio | 2026-07-19 |

## Formato

```
### C-001 — <restricción>
- **Tipo:** técnica | negocio | legal | tiempo | recursos
- **Descripción:** en qué consiste la restricción.
- **Origen:** quién o qué la impone.
- **Implicación:** cómo condiciona el trabajo.
- **Fecha:** YYYY-MM-DD
```

---

## Restricciones

### C-001 — Timebox del prototipo: 15 días hábiles, freeze al día 10

- **Tipo:** tiempo
- **Descripción:** 3 semanas calendario / **15 días hábiles**, arrancando el lunes siguiente al
  cierre de la entrevista. **Feature freeze al terminar el día hábil 10** (cierre de semana 2);
  los 5 días restantes son solo para estabilizar, corregir y dejar presentable. Lo que no entró
  antes del día 10 no entra: pasa a la lista del MVP.
- **Origen:** Analista de Negocios. No es arbitrario: el Gerente General presenta avances al comité
  el primer lunes del mes siguiente y necesita algo que se pueda tocar, no diapositivas.
- **Implicación:**
  - Es distinto del plazo de 6 meses del proyecto completo (C-002). No confundirlos.
  - **Alerta temprana obligatoria:** si en el **día 7 u 8** se ve que el alcance no cabe, se avisa
    en ese momento, no el día 14. El humano prefiere recortar a tiempo que recibir una sorpresa.
- **Fecha:** 2026-07-19

### C-002 — Presupuesto 45K USD y plazo de 6 meses del proyecto

- **Tipo:** recursos
- **Descripción:** el proyecto completo dispone de 45.000 USD y 6 meses.
- **Origen:** Gerente General.
- **Implicación:** cualquier asunto que toque presupuesto o plazo **no lo deciden ni el equipo ni el
  Analista de Negocios**. Se le avisa a él y él escala al Gerente General. El constructor no escala
  directamente a los gerentes.
- **Fecha:** 2026-07-19

### C-003 — Contraparte única: Analista de Negocios, con SLA de 4 horas

- **Tipo:** negocio
- **Descripción:** durante las 3 semanas del prototipo, el **Analista de Negocios** es la contraparte
  única y tiene la última palabra sobre el alcance. No se consulta a otros para resolver
  "¿esto entra o no entra?".
- **Origen:** Analista de Negocios.
- **Implicación:**
  - **Protocolo de desbloqueo:** responde en **menos de 4 horas hábiles**. Vencido el plazo, el
    constructor tiene autorización para tomar **la decisión que menos alcance agregue** y seguir,
    informando después; el humano la asume.
  - **Límites de su autoridad:** presupuesto y plazo son del Gerente General (C-002); cambios en la
    operación real (turnos, asignación de camiones, exigencias a conductores) son del Gerente de
    Operaciones.
  - **Veto desdoblado del Analista de Operaciones:** *sin* veto sobre la lógica del algoritmo
    (dárselo convertiría el proyecto en automatizar el desorden actual del Excel); *con* veto de
    hecho sobre la **utilizabilidad** de la programación resultante. Frase textual del humano:
    *"el analista no diseña la programación, pero si el analista no la puede confirmar, la
    programación está mal"*. No lo resuelve él solo: escala vía el Analista de Negocios al Gerente
    de Operaciones.
  - Conductores y clientes son **observados, no consultados** durante el prototipo.
- **Fecha:** 2026-07-19

### C-004 — Exclusiones del prototipo declaradas por el cliente

- **Tipo:** negocio
- **Descripción:** quedan **fuera** del prototipo: validación de correo electrónico, login real con
  Google o Apple, y **cualquier cosa fuera del camino feliz**. La seguridad de datos está marcada en
  el brief como restricción innegociable, pero su discusión corresponde al MVP.
- **Origen:** Analista de Negocios (reafirmadas en la entrevista sobre lo ya escrito en el brief).
- **Implicación:**
  - Lo excluido es el **mecanismo**, no la presencia visual de la opción (ver D-003).
  - Dentro del alcance: registro de cliente y sus sitios, solicitud de recolección con material,
    tamaño, fecha y hora, programación automática con confirmación del analista, y seguimiento con
    la convención de colores.
  - **No hay cálculo automático de retraso.** Distinción declarada: un **hecho reportado por una
    persona** (el conductor reporta recolección parcial o fallida → amarillo/rojo) sí entra; un
    **estado deducido por el sistema** (retraso calculado contra el reloj) no, porque exigiría fijar
    tolerancias que son competencia del Gerente de Operaciones.
- **Fecha:** 2026-07-19
