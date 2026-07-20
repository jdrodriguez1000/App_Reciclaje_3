# Decisions (ADR ligero)

> Registro de decisiones importantes (Architecture Decision Records simplificados).
> Una decisión aquí es vinculante hasta que otra decisión posterior la reemplace explícitamente.

## Índice

> Mantener sincronizado: al registrar o cambiar el estado de una decisión, actualizar su fila aquí.
> Buscar por ID (`D-XXX`) para localizar la decisión sin leer todo el archivo.

| ID | Decisión | Estado | Fecha |
|---|---|---|---|
| D-001 | Ventana única de auto-confirmación: 5 minutos | aceptada | 2026-07-19 |
| D-002 | Asignación por zona y disponibilidad, con tres reglas duras | aceptada | 2026-07-19 |
| D-003 | Registro simple + botones Gmail/Apple visibles pero inertes | aceptada | 2026-07-19 |
| D-004 | Correo real; WhatsApp y push simulados y marcados | aceptada | 2026-07-19 |
| D-005 | Rejilla material × tamaño (9 celdas) para el tipo de camión | aceptada | 2026-07-19 |
| D-006 | Sin pantalla de Administrador; staff precargado | aceptada | 2026-07-19 |
| D-007 | Gatekeeper del prototipo: cuatro criterios conjuntivos | aceptada | 2026-07-19 |

## Formato

```
### D-001 — <título de la decisión>
- **Estado:** propuesta | aceptada | reemplazada por D-XXX
- **Fecha:** YYYY-MM-DD
- **Contexto:** qué situación obliga a decidir.
- **Decisión:** qué se decidió.
- **Alternativas consideradas:** opciones descartadas y por qué.
- **Consecuencias:** implicaciones (positivas y negativas).
```

---

## Registro

### D-001 — Ventana única de auto-confirmación: 5 minutos

- **Estado:** aceptada
- **Fecha:** 2026-07-19
- **Contexto:** El brief tenía dos relojes en conflicto (ambigüedad A2): confirmación al cliente
  en 5 minutos, pero hasta 1 hora para que el Analista de Operaciones confirmara. El humano
  reconoció que chocaban y que no lo había notado.
- **Decisión:** un solo reloj de **5 minutos**. Si el analista no confirma en ese lapso, el sistema
  confirma la fecha y hora propuestas y notifica al cliente.
- **Alternativas consideradas:** mantener la hora como tope (descartada: 40 minutos de espera
  reproducen exactamente el problema que el proyecto viene a resolver).
- **Consecuencias:**
  - El mensaje en pantalla **no promete un número**: "estamos validando la fecha y hora, le
    confirmamos en breve". Así el tiempo se puede mover sin desmentir la interfaz.
  - Se puede bajar a 1 minuto **solo** si 5 hace incómoda la demo. Nunca dos números conviviendo.
  - Aplazado a MVP: cuál es la ventana real y si depende del horario o del volumen.

### D-002 — Asignación por zona y disponibilidad, con tres reglas duras

- **Estado:** aceptada
- **Fecha:** 2026-07-19
- **Contexto:** El brief declaraba como duda abierta (ambigüedad A3) qué algoritmo usar para
  asignar rutas y conductores. El timebox de 15 días hábiles no admite un optimizador real.
- **Decisión:** asignar al **conductor disponible en la zona** del sitio de recolección para esa
  fecha y hora. La zona es un campo del sitio. Tres reglas duras verificables:
  1. **Sin cruces:** un conductor no puede quedar con dos recolecciones a la misma hora.
     El humano la declara condición sin la cual el prototipo no le sirve.
  2. **Camión correspondiente** al material y tamaño (ver D-005).
  3. **Toda solicitud del camino feliz termina asignada** — sin estado "pendiente de asignación"
     ni solicitudes huérfanas.
- **Alternativas consideradas:** "conductor más cercano" (descartada por exigir distancias reales);
  optimizador de rutas (descartado por costo frente al timebox).
- **Consecuencias:**
  - Las reglas 1 y 3 solo se cumplen a la vez si los datos de demo tienen holgura suficiente
    (ver D-006). El guion de la demo queda atado a esos datos: una solicitud improvisada fuera
    del guion puede caer en el caso que se decidió no cubrir.
  - Aplazado a MVP: optimización real con distancias y tráfico, multi-parada y orden de paradas,
    balanceo de carga, reasignación automática tras fallo de recolección.
  - **Atribución:** acotar la optimización fue decisión explícita del humano, no sugerencia del agente.

### D-003 — Registro simple + botones Gmail/Apple visibles pero inertes

- **Estado:** aceptada
- **Fecha:** 2026-07-19
- **Contexto:** Ambigüedad A1 — el flujo del brief describía validación de correo/Gmail/Apple,
  pero las exclusiones del mismo brief excluían esa validación. Conflicto de redacción, no de criterio.
- **Decisión:** registro real de **nombre + correo + contraseña**, sin link de confirmación, entrada
  inmediata. En la misma pantalla, botones de Gmail y Apple **visibles pero desactivados**,
  etiquetados "próximamente", inertes al tocarlos.
- **Alternativas consideradas:** botones que parecen funcionar sin validar por dentro (descartada:
  pierde credibilidad si alguien pregunta en el comité); omitir Gmail/Apple del todo (descartada:
  el comité debe ver hacia dónde va el producto).
- **Consecuencias:**
  - **Principio de diseño reutilizable, formulado por el humano: "enseñar un plano, no una fachada
    de cartón".** Aplica más allá de este caso (ver D-004).
  - La exclusión del brief sigue vigente y deja de contradecir al flujo: lo excluido es el
    **mecanismo** (verificación y OAuth real), no la **presencia visual** de la opción.
  - **Deuda conocida y declarada** (no descuido): sin verificación, cualquiera se registra con un
    correo inventado. Debe poder responderse "lo sabemos y está en la lista" si alguien lo pregunta.
  - Aplazado a MVP: verificación de correo, ligada a la restricción de seguridad de datos (C-004).

### D-004 — Correo real; WhatsApp y push simulados y marcados

- **Estado:** aceptada
- **Fecha:** 2026-07-19
- **Contexto:** El brief menciona confirmaciones por email, WhatsApp y push. Integrarlos todos de
  verdad no cabe en 15 días hábiles.
- **Decisión:** **el correo sale de verdad** — un solo canal, proveedor más simple posible, texto
  plano aceptable. WhatsApp y push quedan **simulados** en una bandeja dentro de la app y
  **marcados visiblemente como simulados**.
- **Alternativas consideradas:** simular los tres canales en una bandeja interna (descartada: si la
  notificación vive dentro de la app, el cliente igual tiene que entrar a buscarla — es la misma
  dinámica de perseguir el dato que el proyecto viene a romper).
- **Consecuencias:**
  - **CRITERIO GENERAL declarado por el humano, con fuerza de regla autónoma para el constructor:**
    *simular todo lo que sea trámite externo* (WhatsApp Business, cuentas de desarrollador, OAuth
    Google/Apple), porque ahí el tiempo no depende del equipo; *construir de verdad lo que demuestre
    la hipótesis*. Sirve para resolver casos que nunca se preguntaron.
  - **Requisito verificable:** el correo debe traer **fecha y hora confirmadas**, no un acuse
    genérico. Si obliga a entrar a la app para ver el dato, la funcionalidad no cumple su propósito
    aunque el correo llegue.
  - **Techo de esfuerzo:** si el correo real cuesta más de un día de trabajo, se detiene y se avisa.
  - Segunda aplicación del principio "plano, no fachada de cartón" (D-003).

### D-005 — Rejilla material × tamaño (9 celdas) para el tipo de camión

- **Estado:** aceptada
- **Fecha:** 2026-07-19
- **Contexto:** La regla dura 2 de D-002 exige correspondencia camión ↔ material + tamaño, pero el
  brief no define ni los tipos de camión ni la tabla.
- **Decisión:** **rejilla material × tamaño** — 3 materiales (cartón, vidrio, otro) × 3 tamaños =
  **9 filas**, cada una apuntando a un tipo de camión. Varias filas pueden apuntar al mismo camión
  (se esperan 3-4 tipos, no 9). Ninguna celda queda ambigua.
- **Alternativas consideradas:** etiquetar los camiones colapsando material y tamaño en una sola
  letra (**refutada por el humano**: "Tipo B = vidrio/frágil" y "Tipo C = carga grande" se solapan
  — el vidrio grande cabría en los dos y el sistema no podría desambiguar).
- **Consecuencias:**
  - **Distinción de competencias que refina C-003:** la **estructura** de la tabla la decide el
    Analista de Negocios (es diseño); el **contenido** —qué vehículos existen y qué carga cada uno—
    es del Gerente de Operaciones (es operación real).
  - Se construye con tabla **provisional marcada como tal** hasta el día hábil 3 (ver A-001, T-003).
  - **Los tamaños tienen dos representaciones:** la etiqueta interna del eje de la rejilla y el
    texto cara al cliente, que debe usar referencias físicas comprensibles — "cabe en el baúl de un
    carro" / "necesita una camioneta" / "necesita un camión", no "pequeño/mediano/grande" abstracto.

### D-006 — Sin pantalla de Administrador; staff precargado

- **Estado:** aceptada
- **Fecha:** 2026-07-19
- **Contexto:** El brief asigna al Administrador el registro de conductores, analistas y gerentes,
  pero ese rol quedó fuera de la prioridad declarada.
- **Decisión:** **no se construye** la pantalla del Administrador. Analista, conductores y gerentes
  quedan **precargados** con credenciales funcionales; cada rol debe poder entrar y ver su pantalla.
  El rol se explica verbalmente en la demo y se construye en el MVP.
- **Alternativas consideradas:** construir el flujo de creación de usuarios (descartada: ~2 días de
  15 en una pantalla que el comité ha visto mil veces en cualquier sistema).
- **Consecuencias:**
  - **Criterio generalizable:** el Administrador es un rol de **puesta en marcha**, no parte del
    recorrido a demostrar. Mismo razonamiento aplicado a camiones y conductores en D-002.
  - **Requisito de calidad de los datos (verificable, no estético):** datos realistas — nombres de
    persona verosímiles, correos con dominio de la empresa, placas con formato colombiano real.
    Prohibidos explícitamente `analista1`, `conductor_test`, `prueba@prueba.com`. Razón: los datos
    de juguete restan credibilidad delante del Gerente General y cuestan lo mismo.
  - **Requisito de volumen (dependencia cruzada):** el juego de datos debe satisfacer a la vez la
    regla dura 1 de D-002 (sin cruces) y el criterio 2 de D-007 (tres solicitudes en la misma
    franja). Modo de fallo advertido: con dos conductores y tres solicitudes simultáneas la demo se
    cae por falta de datos y parece un defecto del software.

### D-007 — Gatekeeper del prototipo: cuatro criterios conjuntivos

- **Estado:** aceptada
- **Fecha:** 2026-07-19
- **Contexto:** El brief fija adopción del 60% y NPS > 85%, pero un prototipo de camino feliz de
  3 semanas no tiene clientes reales y no puede medir ninguna de las dos. Además, el humano declaró
  que el verdadero falsador de su hipótesis es otro: el **volumen de llamadas de seguimiento**.
- **Decisión:** separar horizontes. Adopción y NPS son del **proyecto a 6 meses**. El gatekeeper del
  **prototipo** son cuatro criterios, **los cuatro se cumplen o no pasa**:
  1. **Camino feliz completo, en vivo, sin trampas.** De principio a fin ante el comité. Si hay que
     explicar por qué algo no se puede mostrar, ya no pasó.
  2. **Tres solicitudes mínimo**, en la misma franja horaria, con materiales y tamaños distintos.
     Una sola no demuestra nada.
  3. **Un Analista de Operaciones real lo opera en frío**, sin entrenamiento previo. Debe entender
     sin que nadie le explique y **confirmar sin querer reprogramar**. El de mayor peso declarado.
  4. **El Gerente de Operaciones dice que le sirve, en voz alta.** "Está bonito" no es un sí.
- **Alternativas consideradas:** heredar adopción y NPS como criterio del prototipo (descartada:
  el humano se negó explícitamente a fingir que se pueden medir en 3 semanas).
- **Consecuencias:**
  - El criterio 3 es el **proxy explícito de la hipótesis**: si quien opera no confía en lo que
    propone el sistema, el cliente tampoco, y se vuelve al Excel.
  - **Riesgo logístico:** el criterio 3 es el único que no depende de construir bien sino de
    agendar (T-004), y **choca con el criterio 1** — un usuario en frío hará cosas que el guion no
    previó. Deben separarse en dos sesiones distintas (T-007).
  - Sin el compromiso verbal del criterio 4, el MVP arrancaría sin dueño real.
