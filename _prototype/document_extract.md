# Extracto del documento del cliente — ReciclApp

## Meta

- **Proyecto:** ReciclApp
- **Documento origen:** _context/client_brief.md
- **Formato / extensión:** md
- **Extraído por:** onboarding-reader
- **Fecha:** 2026-07-19
- **Confirmado por el humano:** sí
- **Estado:** cerrado

## Cobertura

| Área | Tema | Estado | Qué falta (si parcial) |
|---|---|---|---|
| §1 | Objetivo y contexto | cubierta | — |
| §2 | Hipótesis de valor central | parcial | El documento describe el problema (dispersión del canal de solicitud) y el objetivo, pero no formula una afirmación falsable explícita; el interviewer debe confirmar la hipótesis de valor central con el cliente |
| §3 | Tipo de prototipo dominante | n/a | No se le pide al cliente: lo deduce el Descubridor |
| §4 | Stakeholders | parcial | Interés/expectativa está declarado para cada stakeholder, pero no se declara el "poder de decisión" de ninguno |
| §5 | Actores | cubierta | — |
| §6 | Camino feliz + medio por actor | parcial | El método/algoritmo de asignación de rutas y conductores no está definido (el propio cliente lo declara como duda, §10 del brief); además hay un conflicto interno de tiempos de confirmación (ver Ambigüedades A2) que el interviewer debe resolver |
| §7 | Gatekeeper | parcial | Hay métrica y umbral (60% de adopción, NPS > 85%) pero no se declara el método de medición (cómo y sobre qué universo se calculan) |
| §8 | Timebox | parcial | El documento da un plazo general del proyecto (6 meses) pero no un timebox específico del prototipo ni el momento de feature freeze |
| §9 | Exclusiones | cubierta | — |
| §10 | Split por audiencia (opcional) | n/a | El documento no plantea necesidad de artefactos segmentados por audiencia; nada indica que el proyecto lo justifique |

## Extractos por área

### §1 — Objetivo y contexto

> "La empresa Recicladora Oriente Verde, quiere crear una aplicacion para que sus clientes soliciten la recoleccion del reciclaje a traves de esa aplicacion y asi despues ellos organizar el despacho de camiones y conductores para recolectar ese material."
> — client_brief.md, sección "1. Qué problema quiero resolver"

> "Hoy en dia, el servicio se presta a traves de una llamada telefonica, whastapp o por medio de un correo electronico. Esto no es centralizado y genera desorden, a veces no se leen los correos electronicos o los mensajes de WhastApp a tiempo... ESto los esta llevando a tener problemas con sus clientes y con los equipos de recoleccion de material."
> — client_brief.md, sección "1. Qué problema quiero resolver"

### §2 — Hipótesis de valor central

> "El proyecto será existoso si el 60% de mis clientes actuales utilizan la aplicacion para solicitar sus pedidos de recoleccion de datos. Pero ademas quiero tener un NPS superior al 85%."
> — client_brief.md, sección "2. Cómo sabría que esto funcionó"

> "Tambien si logramos que el equipo de recoleccion de material, logra trabajar con esta aplicacion y organizar los camiones y conductores que realizan la recoleccion."
> — client_brief.md, sección "2. Cómo sabría que esto funcionó"

### §4 — Stakeholders

> "1. EL primer interesado es el Gerente General de la compañia, el es el patrocinador principal de la solucion y quien actualmente esta soportando todas las quejas de sus clientes. El espera que los clientes usen la aplicacion, pero sobre todo que el numero de quejas disminuya a casi cero por no recoleccion de material segun lo pactado."
> — client_brief.md, sección "3. Quién tiene interés en esto"

> "2. El Gerente de Operaciones, es el segundo interesado principal, lo que mas espera es tener orden y control total del proceso por medio de la solucion."
> — client_brief.md, sección "3. Quién tiene interés en esto"

> "3. Los Analistas de Operaciones: Son los encargados de asignar conductores y camiones para la recoleccion del material segun la disponibilidad de estos. Es importante que la aplicacion les entregue la mejor planeacion posible..."
> — client_brief.md, sección "3. Quién tiene interés en esto"

> "4. Los conductores de vehiculos quienes de forma organizada veran la programacion de sus recorridos, pudiendo de esta forma poder recolectar el material sin necesidad de realizar cambios de ultimo momento..."
> — client_brief.md, sección "3. Quién tiene interés en esto"

> "5. Los usuarios (clientes) quienes utilizan la aplicacion para realizar la solicitud de pedido de recoleccion de material reciclado. Ellos esperan que la empresa recoja el material segun lo programado por la aplicacion."
> — client_brief.md, sección "3. Quién tiene interés en esto"

### §5 — Actores

> "1. El usuario (cliente) es el principal usuario, es quien solicita por medio de la solucion la recoleccion del material reciclado."
> — client_brief.md, sección "4. Quién va a usarlo"

> "2. El Analista de Operaciones: Es quien recibe las solicitudes de recoleccion de material realizadas por los usuario y verifica y despues confirma la programacion entregada por la aplicacion..."
> — client_brief.md, sección "4. Quién va a usarlo"

> "3. El Conductor quien ingresa a la aplicacion para visualizar las recolecciones que debe realizar segun el recorrido."
> — client_brief.md, sección "4. Quién va a usarlo"

> "4. El Gerente de Operaciones: Quien ingresa a la aplicacion para visualizar el plan de trabajo de recoleccion de material reciclado, ademas ve indicadores como el porcentaje de recoleccion a tiempo, los principales motivos de no recoleccion, entre otros..."
> — client_brief.md, sección "4. Quién va a usarlo"

> "5. El Gerente General, quien ingresa a la aplicacion para saber el nivel de NPS, el porcentaje / numero de usuarios que esta utilizando la aplicacion, ademas tambien puede ver otros KPIS..."
> — client_brief.md, sección "4. Quién va a usarlo"

> "6. El Administrador: Es un usuario tecnico (sistemas) quien registra en la aplicacion a usuarios que no son clientes de la empresa... En general es quien administra la aplicacion y es responsable de saber que esta siempre disponible."
> — client_brief.md, sección "4. Quién va a usarlo"

### §6 — Camino feliz + medio por actor

> "1. El usuario (cliente): Este se registra en la aplicacion... Despues de Registrar los sitios puede solicitar la recogida del material. Para esto el usaurio debe primero informar el material que se va recolectar como carton, vidrio u otro y el tamaño... ademas registra una fecha y hora de recoleccion y por ultimo confirma la solicitud de pedido. ... Lo usa principalmente en una app en su telefono movil."
> — client_brief.md, sección "5. Cómo lo usarían, paso a paso"

> "Por pantalla este usuario puede ir observando el estado de la solicitud de recoleccion como un flujo, ejemplo: 1.1. Solicitud con fecha y hora. 1.2. Confirmacion solicitud - Fecha y hora. 1.3. Confirmacino de recoleccion - Fecha - hora. 1.4. Inicio de recoleccion - Fecha y hora. 1.5. Recoleccion - Fecha y hora. 1.6. Cierre Recoleccion - Fecha - hora."
> — client_brief.md, sección "5. Cómo lo usarían, paso a paso"

> "2. El usuario Analista de OPeraciones: Ingresa a la aplicacion por medio de usuario y contraseeña, su labor principal es revisar la programacion entregada por la aplicacion y confirmarla. Si este usuario no confirma en un plazo maximo de 1 hora, la aplicacion asume la confirmacion. Ese usuario es el unico que puede reprogramar una recoleccion pero solo lo puede hacer antes de la cofrimacion de fecha y hora... Lo usa principalmente en una web en su equipo de computo."
> — client_brief.md, sección "5. Cómo lo usarían, paso a paso"

> "3. El conductor ingresa a la aplicacion por medio de usuario y contraseña, y conoce la programación de las recolecciones qeu debe tener en su turno para ese dia. El conductor cada vez que recoge informacion lo notifica a traves de la aplicacion... Lo usa principalmente en una app en su telefono movil."
> — client_brief.md, sección "5. Cómo lo usarían, paso a paso"

> "4. El Gerente de operaciones ingresa por medio de usuario y contraseña, cada vez que ingresa observa un dashboard con los principales KPIs de su rol. Lo usa principalmente en una web en su equipo de computo."
> — client_brief.md, sección "5. Cómo lo usarían, paso a paso"

> "6. El administrdor ingresa por medio de un usuario y contraseña, cada vez que ingresa entra a un tablero de control que le permite registrar, inactivar usuarios, asignar segun el rol a los usuarios... Lo usa principalmente en una web en su equipo de computo."
> — client_brief.md, sección "5. Cómo lo usarían, paso a paso"

### §7 — Gatekeeper

> "El proyecto será existoso si el 60% de mis clientes actuales utilizan la aplicacion para solicitar sus pedidos de recoleccion de datos. Pero ademas quiero tener un NPS superior al 85%."
> — client_brief.md, sección "2. Cómo sabría que esto funcionó"

> "1. Que el 60% de los clientes utilice la aplicacion para realizar la solicitud de pedidos de recoleccion de material. 2. Que el NPS sea superior al 85%. 3. Que no se utilicen otras aplicaciones para organizar la recogida de material reciclado."
> — client_brief.md, sección "6. Cómo mediríamos el éxito"

### §8 — Timebox

> "La aplicacion se debe construir en un plazo maximo de 6 meses."
> — client_brief.md, sección "7. Plazos y restricciones"

### §9 — Exclusiones

> "1. Validacion de correo electronico. 2. Tampoco validacion de correo con gmail o con apple 3. Se debe seguir el camino feliz."
> — client_brief.md, sección "8. Qué NO quiero que se haga ahora"

## Ambigüedades detectadas

| # | Área | Qué dice el documento | Por qué es ambiguo |
|---|---|---|---|
| A1 | §6 ↔ §9 | §6: "este registro es por email con validacion de correo, o puede ser utilizando sus corros de gmail o de apple" (sección "5. Cómo lo usarían, paso a paso") **vs.** §9: "1. Validacion de correo electronico. 2. Tampoco validacion de correo con gmail o con apple" (sección "8. Qué NO quiero que se haga ahora") | Contradicción directa: el camino feliz del generador describe el registro con validación de correo/gmail/apple como parte del flujo, mientras que la sección de exclusiones declara que esa misma validación NO debe hacerse ahora |
| A2 | §6 (Generador) ↔ §6 (Operador) | Generador: "Al cabo de 5 minutos recibirá un email, un mensaje de Whastapp o una notificacion push donde se le informa la fecha y hora confirmada para la recoleccion" (sección 5, punto 1) **vs.** Operador (Analista): "Si este usuario no confirma en un plazo maximo de 1 hora, la aplicacion asume la confirmacion" (sección 5, punto 2) | Conflicto de tiempos: no queda claro si la confirmación real ocurre en 5 minutos o puede tardar hasta 1 hora (plazo del analista antes de auto-confirmarse) |
| A3 | §6 | "La duda que tengo es como la aplicaicon asigna la programacion para los conductores, utiliza algun algoritmo de optimizacion de rutas o cual otro puede utilizar." — client_brief.md, sección "10. Dudas que tengo yo" | Vaguedad declarada por el propio cliente: el método/algoritmo de asignación de rutas y conductores no está definido |

## Fuera de alcance del descubrimiento

- Presupuesto del proyecto: "El presupuesto es 45K USD." (sección "7. Plazos y restricciones")
- Restricción de seguridad de datos: "Politica de seguridad de datos de los clientes." (sección "7. Plazos y restricciones") — no mapea a ninguna área §1–§10 del discovery
- "No se tiene referencia de alguna aplicacion." (sección "9. Referencias, ideas previas y material existente") — sin contenido relevante para el descubrimiento
