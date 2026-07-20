# Entregable de descubrimiento — ReciclApp

## Meta

- **Proyecto:** ReciclApp
- **Cliente / solicitante:** Recicladora Oriente Verde — contraparte para el descubrimiento: Jota D, Analista de Negocios (última palabra sobre el alcance del prototipo; ver §4)
- **Descubridor:** onboarding-interviewer (entrevista) + onboarding-reader (ingesta del brief) — síntesis por onboarding-writer
- **Fecha:** 2026-07-19
- **Timebox del descubrimiento:** 45 min / 20-25 preguntas acordadas; cerrada en 11 preguntas de contenido por suficiencia declarada por el entrevistado (Q12), no por agotamiento del timebox
- **Procedencia de los insumos:** log: cerrada · extracto: confirmado (Confirmado por el humano: sí; Estado: cerrado)
- **Estado:** cerrado
- **Aprobado por el humano:** sí (2026-07-20)

## 1. Objetivo y contexto

Recicladora Oriente Verde quiere centralizar en una sola aplicación la solicitud de recolección de material reciclado, hoy dispersa entre llamada telefónica, WhatsApp y correo electrónico. Esa dispersión genera desorden operativo (mensajes no leídos a tiempo, promesas hechas bajo presión que los camiones no pueden cumplir) y deteriora la relación con los clientes. La app debe permitir que el cliente solicite la recolección y que, detrás, la empresa organice el despacho de camiones y conductores de forma programada y confiable.

## 2. Hipótesis de valor central

> "El cliente deja de llamar cuando la app le cumple. Nuestra apuesta es que si la solicitud recibe una confirmación firme y esa recolección efectivamente ocurre en la fecha y hora confirmada, el cliente deja de usar teléfono, WhatsApp y correo — no porque la app sea más cómoda, sino porque ya no necesita perseguirnos. Y eso solo es posible si detrás la programación de camiones y conductores es real y se cumple." (Q5)

**Falsador declarado:** no es la tasa de adopción, sino el **volumen de llamadas de seguimiento** ("¿sí van a venir?"). Si la gente usa la app y aun así sigue llamando a confirmar, la hipótesis está muerta aunque la adopción llegue al 60% (Q5).

**Riesgo asumido a conciencia:** al registrar cada incumplimiento con fecha, hora y estado en rojo, la app puede documentar el propio fracaso operativo si la parte de operaciones no funciona (Q5).

## 3. Tipo de prototipo dominante

- **Tipo dominante:** deseabilidad, con una capa mínima de lógica funcional real que la sostiene (no es solo un mockup estático).
- **Por qué:** el riesgo que el cliente más quiere descartar no es técnico (la asignación se resuelve con una regla simple, ya decidida en Q3) sino de confianza/adopción: que el Analista de Operaciones confíe en la programación propuesta sin querer reprogramar, y que el cliente deje de llamar. El criterio 3 del Gatekeeper (§7) — un analista real operando en frío — es explícitamente el proxy de este riesgo de deseabilidad, no de factibilidad.
- **Secuencia prevista:** deseabilidad primero (y única para este prototipo); la factibilidad real de la optimización de rutas queda aplazada al MVP (Q3).

## 4. Stakeholders

| Stakeholder | Interés / expectativa | Poder de decisión |
|---|---|---|
| Gerente General | Patrocinador principal; espera adopción de clientes y que las quejas por no recolección bajen a casi cero (extracto §4) | Alto — decide presupuesto (45K USD) y plazo del proyecto completo (6 meses); se escala, no lo decide el Analista de Negocios ni el prototipador (Q6) |
| Gerente de Operaciones | Espera orden y control total del proceso (extracto §4) | Alto — decide todo lo que cambie la operación real (turnos, asignación de camiones, exigencias a conductores); su "sí" explícito es el criterio 4 del Gatekeeper (Q6, Q7) |
| Analista de Negocios (Jota D) | Contraparte única del descubrimiento y del prototipado en estas 3 semanas | Alto para el alcance del prototipo — última palabra sobre "¿esto entra o no entra?"; protocolo de desbloqueo: responde en <4h hábiles o el constructor decide lo que menos alcance agregue (Q6) |
| Analistas de Operaciones | Esperan la mejor planeación posible de la app (extracto §4) | Medio — veto desdoblado: no tienen veto sobre el algoritmo de asignación, pero sí veto de hecho sobre si la programación es utilizable (si no la pueden confirmar, es alerta seria escalada vía el Analista de Negocios) (Q6) |
| Conductores | Esperan programación organizada sin cambios de último momento (extracto §4) | Bajo — observados, no consultados, en estas 3 semanas; sus señales se anotan para el MVP (Q6) |
| Usuarios / clientes | Esperan que la recolección ocurra según lo programado (extracto §4) | Bajo — observados, no consultados, en estas 3 semanas (Q6) |

## 5. Actores (taxonomía por defecto — §4.3)

| Arquetipo | Actor concreto | Estado | Notas |
|---|---|---|---|
| **Generador** | Usuario (cliente) | presente | Origina el valor central: solicita la recolección. Prioridad explícita del cliente junto con el Operador (Q1: "el corazón" del prototipo) |
| **Operador** | Analista de Operaciones (principal) + Conductor (secundario) | presente | El Analista de Operaciones revisa/confirma la programación (flujo priorizado en profundidad, Q1–Q11). El Conductor también opera —ve su turno y reporta el resultado de la recolección (verde/amarillo/rojo)— pero no se elicitó en la misma profundidad; su flujo se declara pero no se detalla más allá de lo que consta en el brief |
| **Administrador** | Administrador (rol técnico de sistemas) | presente pero fuera del camino feliz construido | El rol existe y está descrito (registra conductores, analistas, gerentes), pero para el prototipo se precarga con credenciales listas; la pantalla de administración de usuarios no se construye (Q11) — aplazado a MVP |

**Nota adicional (fuera de la taxonomía estricta, declarada por transparencia):** Gerente General y Gerente de Operaciones también "usan" la app vía dashboards de KPIs (extracto §5), pero ese uso quedó fuera de la priorización del cliente (Q1) y es un hueco declarado, no un actor desarrollado en este descubrimiento (ver §9).

## 6. Camino feliz por actor

### Generador — Usuario (cliente) · **[obligatorio · lo construye el Prototipador primero]** · medio: app en teléfono móvil

1. Se registra con nombre, correo y contraseña, sin verificación real (sin link de confirmación); los botones de Gmail y Apple están visibles pero desactivados, con etiqueta "próximamente" — no hacen nada al tocarlos (decisión propia del cliente, Q4). **Deuda conocida y declarada:** sin verificación, cualquiera puede registrarse con un correo inventado; aceptado para la demo.
2. Registra uno o varios sitios de recolección (nombre + dirección) (extracto §6).
3. Solicita la recolección informando: material (cartón, vidrio u otro), tamaño —con etiquetas orientadas al cliente: "cabe en el baúl de un carro" / "necesita una camioneta" / "necesita un camión" (Q10)—, y fecha y hora deseadas.
4. Confirma la solicitud. La pantalla no promete un número de minutos: dice algo como "estamos validando la fecha y hora, le confirmamos en breve" (restricción de copy, Q2).
5. A los 5 minutos (ventana única de confirmación/auto-confirmación, decisión del prototipo que unifica los dos tiempos en conflicto del brief — ver discrepancia más abajo) recibe la fecha y hora confirmadas por **correo electrónico real** (proveedor simple, texto plano si hace falta; debe traer la fecha/hora confirmadas, no un acuse genérico) y, simuladas dentro de una bandeja de notificaciones interna marcada visiblemente como "simulado", por WhatsApp y push (Q9).
6. Ve el estado avanzar en pantalla con la convención de colores confirmada del brief: **verde = realizado**, **gris claro = pendiente**; si la recolección se llevó a cabo exitosamente usa verde, si fue parcial usa amarillo, si no se pudo llevar a cabo usa rojo; el cierre usa la misma convención (cita literal, brief sección 5, líneas 56 y 58 — ver nota de incidente al final de este documento). Pasos del flujo: Solicitud → Confirmación de solicitud → Confirmación de recolección → Inicio de recolección → Recolección → Cierre (extracto §6). **En la demo, el camino feliz recorre solo gris → verde**; amarillo/rojo (reporte del conductor) quedan funcionales pero fuera del recorrido principal (Q8).
7. Resultado: la solicitud termina con un conductor y un camión asignados sin cruces (regla dura 1), con el tipo de camión correspondiente al material y tamaño informados (regla dura 2, tabla 3×3 material×tamaño — estructura confirmada, contenido pendiente hasta día hábil 3, ver §9), y sin quedar nunca en estado "pendiente de asignación" (regla dura 3) (Q3).

**Discrepancia declarada entre brief y entrevista (A2):** el brief describía dos tiempos de confirmación distintos — 5 minutos para el cliente (extracto §6, Generador) vs. hasta 1 hora para que el Analista de Operaciones confirme antes de la auto-confirmación (extracto §6, Operador). El cliente confirmó en Q2 que son dos cosas distintas que chocaban sin que lo notara. **Decisión (prevalece la entrevista, por ser posterior):** un solo reloj de 5 minutos para el prototipo; lo de la hora se aplaza a MVP como discusión real de carga operativa.

### Operador — Analista de Operaciones (principal) · [bajo demanda, pero priorizado junto al generador] · medio: web en equipo de cómputo

1. Ingresa con usuario y contraseña (cuenta precargada, sin pantalla de administrador — Q11).
2. Revisa la programación entregada automáticamente por la regla de asignación por **zona y disponibilidad** (conductor disponible en la zona del sitio para la fecha/hora solicitada; Q3).
3. Confirma dentro de la ventana de 5 minutos; si no confirma, el sistema auto-confirma con la fecha/hora que la app propuso (Q2).
4. Tiene veto de hecho (no de diseño) sobre si la programación es utilizable: si no puede confirmarla, lo escala al Analista de Negocios en vez de reprogramar directamente (Q6) — este es el criterio 3 del Gatekeeper (§7), el de mayor peso para el cliente.

**Nota — Conductor (operador secundario, presente pero no detallado en profundidad):** ingresa con usuario y contraseña, ve la programación de su turno del día, y notifica el resultado de cada recolección (exitosa = verde, parcial = amarillo, no realizada = rojo) (extracto §6). No se elicitó más allá de lo que consta en el brief; es la fuente de los estados amarillo/rojo mencionados en el paso 6 del camino del generador.

### Administrador — N/A — ver §5 · medio: — (no se construye en el prototipo)

No se construye una pantalla ni flujo de administración de usuarios. Para la demo, analista, conductores y gerentes ya están creados con credenciales listas, con datos realistas (nombres que suenen a personas, correos con dominio de la empresa, placas de camión con formato colombiano real) y en volumen suficiente para sostener sin cruces las reglas duras y el criterio 2 del Gatekeeper (Q11). Aplazado a MVP.

## 7. Gatekeeper (criterio de salida cuantitativo — §4.3/§4.4)

**Nota de horizonte:** la métrica de adopción (60%) y NPS (>85%) del brief (extracto §7) son del proyecto completo a 6 meses, con clientes reales; el cliente confirmó explícitamente (Q7) que no se pueden medir en un prototipo de 3 semanas y que no se va a fingir que sí. El Gatekeeper de este prototipo es distinto y consta de **cuatro criterios conjuntivos**: los cuatro se cumplen o el prototipo no pasa.

- **Métrica:** cumplimiento simultáneo de los 4 criterios de demo definidos por el cliente (Q7):
  1. Camino feliz completo ejecutado en vivo, sin trampas ni pasos salteados, delante del comité.
  2. Mínimo **3 solicitudes** simultáneas en la misma franja horaria, con materiales y tamaños distintos, sin que ningún conductor quede con citas cruzadas y con el camión correspondiente en cada caso.
  3. Un Analista de Operaciones real opera en frío (sin entrenamiento previo) y confirma la programación **sin querer reprogramarla** — proxy explícito de la hipótesis de valor (§2).
  4. El Gerente de Operaciones dice explícitamente **"sí"** en voz alta al ser preguntado si esto le sirve para organizar su operación ("está bonito" no cuenta como sí).
- **Umbral de éxito:** los **4/4** criterios cumplidos; el fallo de cualquiera de los cuatro invalida el prototipo (criterio conjuntivo, no promedio).
- **Cómo se mide:** observación directa en la demo ante el comité, con un juego de datos de prueba realista y dimensionado (suficientes conductores y camiones precargados para que la demo no falle por falta de datos en vez de por defecto del software); el criterio 3 se mide con un analista real operando sin guion, y el criterio 4 con una pregunta directa al Gerente de Operaciones al cierre de la demo.

## 8. Timebox y feature freeze (§4.3)

- **Duración tope del prototipo:** 3 semanas calendario (15 días hábiles), arrancando el lunes siguiente al cierre de la entrevista de descubrimiento (Q1). Motivo: el Gerente General presenta avances al comité el primer lunes del mes siguiente y necesita algo tocable.
- **Al cerrar el timebox:** feature freeze al cierre del día hábil 10 (fin de la semana 2); los 5 días restantes (11–15) son solo estabilización, corrección y dejar presentable — lo que no entre antes del día 10 pasa a la lista del MVP. Si el alcance no cabe, se avisa el día hábil 7-8, no el día 14 (Q1).
- **Nota:** este timebox es del prototipo, no del plazo general del proyecto (6 meses, extracto §8), que es un horizonte distinto.

## 9. Exclusiones explícitas (§4.3)

- Validación real de correo electrónico (verificación / link de confirmación) — deuda conocida y declarada (Q4; también extracto §9).
- Autenticación real (OAuth) con Google/Apple — botones visibles pero inertes, etiqueta "próximamente" (Q4; también extracto §9).
- WhatsApp Business API real y push notifications reales — simulados en la bandeja de notificaciones interna, marcados visiblemente como simulados (Q9).
- Optimización real de rutas (distancias, tráfico), recorridos multi-parada, balanceo de carga entre conductores/camiones, y reasignación automática por incumplimiento — aplazado a MVP (Q3).
- Estado de "retrasado" calculado automáticamente (tolerancia en minutos, dependencia del tipo de material, camión demorado en ruta) — aplazado a MVP, competencia del Gerente de Operaciones (Q8).
- Pantalla y flujo de administración de usuarios (rol Administrador) — se precargan las cuentas, no se construye la pantalla (Q11).
- Dashboards del Gerente General y del Gerente de Operaciones — sacrificables para este prototipo; construibles "si alcanza el tiempo" y con datos de muestra; **hueco declarado** por decisión explícita del cliente en Q1, no repreguntado en profundidad.
- Contenido definitivo (real) de la tabla camión × material × tamaño — la **estructura** (rejilla 3×3) quedó confirmada y cerrada, pero el **contenido** de las celdas depende del Gerente de Operaciones, comprometido para el día hábil 3; mientras tanto se construye con una tabla **provisional, marcada explícitamente como tal**. **Hueco declarado** (Q10).
- Todo lo que quede fuera del camino feliz del cliente y del Analista de Operaciones (exclusión general reafirmada del brief, extracto §9).

<!-- §10 no aplica: n/a según el extracto (n/a — el documento no plantea necesidad de artefactos
     segmentados por audiencia) y no repreguntado en la entrevista. Sección omitida. -->

---

## Incidente de proceso — constancia de trazabilidad de insumos

`_prototype/document_extract.md` resultó **incompleto**: no capturó la convención de colores del cliente, pese a que estaba íntegramente descrita en `_context/client_brief.md` (sección "5. Cómo lo usarían, paso a paso", líneas 56 y 58 del brief original):

> "Ademas, debe tener una convencion de colores, Verde para realizado y gris claro para pendiente. Ademas cuando la recoleccion se llevo a cabo exitosamente utiliza el color verde, pero si se llevo a cabo de forma parcial utiliza el amarillo y si no se pudo llevar a cabo utiliza el color rojo. El cierre utilizará esta misma convencion."
> — client_brief.md, sección "5. Cómo lo usarían, paso a paso"

> "Ejemplo cuando el cliente solicita la recoleccion el flujo muestra Solicitud en color verde y abajo muestra la fecha y hora de realizacion de la solicitud."
> — client_brief.md, misma sección

Esto llevó a que el `onboarding-interviewer` formulara una pregunta parcialmente redundante (Q8), señalada por el propio cliente como gasto innecesario de su presupuesto de preguntas. La causa raíz es de la etapa de ingesta (`onboarding-reader`), no de la entrevista ni de esta síntesis. Este `discovery.md` se redactó leyendo `interview_document.md`, `document_extract.md` **y** `_context/client_brief.md` directamente (siguiendo la recomendación explícita dejada en el cierre del log), precisamente para recuperar este contenido y evitar que se perdiera de nuevo en esta etapa.
