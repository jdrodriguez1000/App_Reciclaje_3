# Entrevista de descubrimiento (log crudo) — ReciclApp

## Meta

- **Proyecto:** ReciclApp <!-- FUENTE: _context/project.yaml (project.name) -->
- **Entrevistado:** Jota D — Analista de Negocios (rol declarado por el propio entrevistado en Q6; corrige la suposición inicial de "Gerente General")
- **Entrevistador:** onboarding-interviewer
- **Inicio:** 2026-07-19
- **Timebox acordado:** Entrevista: 45 min / 20-25 preguntas (medir por preguntas, no reloj); si a la P25 quedan vacíos importantes, se anotan como supuestos marcados para una segunda ronda corta, sin alargar esta sesión. Prototipo: 3 semanas calendario (15 días hábiles), arranca el lunes siguiente al cierre de esta entrevista; feature freeze al cierre del día hábil 10 (fin semana 2) — los 5 días restantes son solo estabilización; si el alcance no cabe, se avisa el día 7-8, no el día 14.
- **Estado:** cerrada
- **Sección en curso:** — (entrevista cerrada; ver sección Cierre)
- **Extracto documental:** _prototype/document_extract.md

- **Áreas cubiertas por el documento (no se preguntan):** §1, §5, §9 (cubiertas); §3, §10 (n/a)

## Registro de la entrevista

### Q1 · área: §8 — Timebox
**P:** ¿Cuánto tiempo o cuántas preguntas está dispuesto a dedicar a esta entrevista de descubrimiento? Y ya que estamos en el tema: ¿cuál es el timebox específico para este prototipo (no el plazo general del proyecto de 6 meses que ya está en el brief), y en qué momento se congelarían las funcionalidades (feature freeze) antes de darlo por construido?
**R:** Dispongo de 45 minutos, mide en preguntas (20 a 25), no en reloj. Si en la pregunta 25 siguen vacíos importantes, no alargar la sesión: se anotan como supuestos marcados para resolver en una segunda ronda corta — prefiere dos conversaciones enfocadas a una de dos horas. Pide priorizar el flujo del cliente y del Analista de Operaciones (el corazón); los dashboards del Gerente General y del Gerente de Operaciones al final, y si no alcanzan, no pasa nada en esta etapa. Sobre el timebox del prototipo: los 6 meses son del proyecto completo, no del prototipo. Para el prototipo tiene 3 semanas calendario / 15 días hábiles, arrancando el lunes siguiente al cierre de esta entrevista; el motivo es que el Gerente General presenta avances al comité el primer lunes del mes siguiente y necesita algo tocable, no diapositivas. Feature freeze: al terminar el día hábil 10 (cierre de la semana 2); los 5 días restantes son solo para estabilizar, corregir y dejar presentable — lo que no entre antes del día 10 no entra, pasa a la lista del MVP. Alcance dentro del prototipo: registro del cliente y sus sitios de recolección; solicitud de recolección con material, tamaño, fecha y hora; la programación automática y su confirmación por el Analista de Operaciones; el seguimiento del flujo con la convención de colores descrita en el brief. Fuera del alcance: validación de correo, login con Google o Apple, y cualquier cosa fuera del camino feliz (reafirma lo ya escrito en el brief). Los dashboards gerenciales, si alcanzan, con datos de muestra. Pide que si en el día 7 u 8 el alcance no cabe, se le avise en ese momento, no el día 14.

### Q2 · área: §6 / A2 — Conflicto de tiempos de confirmación (RESUELTO)
**P:** En el brief hay dos tiempos distintos para la confirmación de una solicitud: el flujo del cliente dice que recibe la confirmación a los 5 minutos de solicitar la recolección, pero el flujo del Analista de Operaciones dice que este tiene hasta 1 hora para confirmar (o la aplicación auto-confirma). ¿Cómo concilio esto para el camino feliz del prototipo? Por ejemplo: ¿los 5 minutos son el tiempo típico/esperado de respuesta del analista (y la 1 hora es solo el tope máximo antes de auto-confirmar), o son dos cosas distintas que no había notado que chocan?
**R:** Son dos cosas distintas que chocan y el cliente no lo había notado; no hay intención oculta. Los 5 minutos los escribió pensando en el cliente, como promesa en pantalla ("usted pide, y en un ratito le confirmamos"), en reacción a la queja actual de esperar medio día sin noticias. La hora la escribió pensando en el Analista de Operaciones, como tope antes de que el sistema decida solo, por no exigirle respuesta inmediata dado que tiene otras cosas encima. Reconoce el problema: si el analista se demora 40 minutos, el cliente ya lleva 35 sintiéndose engañado — es justo el problema que vino a resolver, así que no puede dejarlo así.

Decisión para el prototipo: un solo número, 5 minutos. La ventana de auto-confirmación del prototipo es de 5 minutos, no de una hora. Si el analista no confirmó en ese lapso, el sistema confirma la fecha y hora que la aplicación propuso, y el cliente recibe su notificación. Un solo reloj, sin dos relojes compitiendo.

Precisión 1 (restricción de copy): el mensaje que ve el cliente al confirmar la solicitud no debe prometer un número; debe decir algo como "estamos validando la fecha y hora, le confirmamos en breve" — así, si el tiempo cambia en el futuro, no hay que desmentir una promesa escrita en pantalla.

Precisión 2 (aplazado a MVP): lo de la hora no se descarta, se aplaza. Es una discusión de operación real (carga de trabajo y turnos de analistas) que no se resolverá en un prototipo de camino feliz. Queda anotado como algo a definir para el MVP: cuál es la ventana real y si depende del horario o del volumen. Para lo que necesita mostrar en 3 semanas, 5 minutos le sirve y demuestra el punto ante el comité.

Precisión 3 (margen de demo): si al construirlo 5 minutos hace la demo incómoda (quedarse esperando frente a la pantalla), se puede bajar a 1 minuto para efectos de demostración — avisar en ese momento. Lo que no quiere es dos números distintos conviviendo.

### Q3 · área: §6 / A3 — Algoritmo de asignación de rutas y conductores (RESUELTO)
**P:** El brief dice textualmente: "la duda que tengo es cómo la aplicación asigna la programación para los conductores, utiliza algún algoritmo de optimización de rutas o cuál otro puede utilizar". Para el prototipo, dado que el feature freeze es al día hábil 10, necesito algo simple que "funcione" en la demo, no un optimizador real. ¿Le sirve que la asignación en el prototipo sea una regla simple —por ejemplo: asignar al conductor disponible más cercano a la zona en la fecha/hora solicitada, o por turno/orden de disponibilidad— dejando la optimización real de rutas (multi-parada, tráfico, capacidad de camión, etc.) para el MVP? ¿O hay alguna regla mínima que sí necesita ver funcionando ahora, como no cruzar a un mismo conductor en dos citas al mismo tiempo?
**R:** Sí, le sirve la regla simple; no pretende un optimizador en tres semanas ni lo necesita para el comité. Lo que quiere demostrar es que el pedido entra por un solo canal y sale con un conductor y un camión asignados — eso es lo que hoy no existe. Qué tan óptima sea esa asignación es "conversación de mes 4, no de mes 1".

Regla de asignación elegida: por **zona y disponibilidad** — el conductor disponible en la zona del sitio de recolección para esa fecha y hora. Descarta explícitamente "el más cercano" porque implica manejar distancias reales, un problema que no quiere pagar todavía. La zona es un campo del sitio, y con eso basta.

Declara esto como **decisión propia** (no sugerencia del agente): entiende que la optimización real es un problema aparte con su propio peso, y que mezclarlo con el prototipo era la forma más rápida de no entregar nada en 3 semanas. Su duda original del brief queda respondida.

**Reglas duras que sí deben verse funcionando en el prototipo** (condición para que el prototipo le sirva):
1. **No doble reserva de conductor:** un conductor no puede quedar con dos recolecciones a la misma hora. Es la que más le importa — si eso falla en la demo frente al Gerente de Operaciones, "se acabó la reunión": sería el mismo desorden que hoy tienen con Excel.
2. **Correspondencia tipo de camión ↔ material y tamaño:** el tipo de camión asignado debe corresponder al material y tamaño informados por el cliente en la solicitud (justamente para eso pidió esos datos en el brief). Bastan tres tipos de camión y una tabla simple de correspondencia; no requiere cálculo de capacidad en kilos.
3. **Toda solicitud del camino feliz termina asignada:** no debe verse un estado "pendiente de asignación" ni solicitudes huérfanas. Si en la demo no hubiera conductor disponible, el prototipo no debe llegar a ese caso — autoriza precargar suficientes conductores y camiones en los datos de prueba/demo (lo llama "dato de demo, no decisión de arquitectura").

**Aplazado explícitamente a MVP** (cerrado, no reabrir en semana 2):
- Optimización de rutas real, con distancias y tráfico.
- Recorridos multi-parada y orden de las paradas.
- Balanceo de carga entre conductores y camiones.
- Reasignación automática cuando un conductor reporta que no pudo recoger.

### Q4 · área: §6 / A1 — Conflicto validación de correo/Gmail/Apple (RESUELTO)
**P:** En el flujo del cliente (§6 del brief) se describe el registro con "validación de correo, o puede ser utilizando sus correos de gmail o de apple", pero en las exclusiones (§9) dice textualmente "Validación de correo electrónico. Tampoco validación de correo con gmail o con apple". Para el prototipo, ¿cómo se registra el cliente entonces? Por ejemplo: ¿el formulario le pide correo/gmail/apple como dato de identificación pero sin verificarlo de verdad (sin enviar link de confirmación, sin OAuth real), o prefiere que el registro sea aún más simple —nombre, correo y contraseña, sin mencionar gmail/apple— y esa parte del flujo que describió no aplica todavía?
**R:** Aclara que el conflicto es de redacción suya, no de criterio: al describir el flujo (§6 de nuestro mapeo) estaba describiendo la aplicación terminada; al escribir las exclusiones (§9 de nuestro mapeo) pensaba en qué no quería que costara tiempo ahora, y no notó que un texto contradecía al otro. La exclusión sigue vigente: no quiere que se gasten días con la verificación de correo ni con las cuentas de desarrollador de Google y Apple, que tienen trámites propios que no controla.

Ninguna de las dos opciones planteadas por el interviewer le convence del todo. La primera (pedir correo/gmail/apple sin verificar nada) no la quiere: poner botones de Gmail/Apple que "parecen funcionar pero por dentro no validan nada" es un problema en la demo frente al Gerente General — si alguien pregunta si ya se puede entrar con Google y la respuesta es "eso es de mentiras", pierde credibilidad justo en la reunión donde la necesita. La segunda (registro simple sin mencionar gmail/apple) le deja corto, porque el ingreso con Gmail y Apple sí es parte de la visión y quiere que el comité lo vea en el mapa, no que crea que se olvidó.

**Decisión propia del cliente (tercera vía, no ofrecida por el interviewer):** el registro real del prototipo es nombre, correo y contraseña, sin link de confirmación — uno se registra y entra de una, ese es todo el mecanismo real. En la misma pantalla, los botones de Gmail y Apple aparecen **visibles pero desactivados**, con una etiqueta tipo "próximamente"; no hacen nada al tocarlos. Así el comité ve hacia dónde va el producto sin que nadie se confunda sobre qué está construido, y no se gasta tiempo en OAuth. Lo describe como "la diferencia entre enseñar un plano y enseñar una fachada de cartón — quiero el plano".

La exclusión de §9 sigue vigente y ya no contradice al flujo: lo excluido es el mecanismo de validación (verificación de correo y OAuth real), no la presencia visual de la opción en la interfaz.

**Deuda conocida y declarada (no descuido):** como no hay verificación, cualquiera puede registrarse con un correo inventado. Para la demo está bien, pero pide explícitamente que quede escrito como deuda conocida, para poder responder "lo sabemos y está en la lista" si el Administrador o alguien de sistemas lo señala en la presentación.

**Aplazado a MVP:** la verificación de correo, ligada a la conversación de seguridad de datos que el brief marca como restricción innegociable — ahí se discutirá en serio quién puede crear cuentas y cómo se prueba que un correo es de quien dice ser.

### Q5 · área: §2 — Hipótesis de valor central (falsable)
**P:** El brief da la métrica de éxito (60% de adopción, NPS > 85%) pero no una hipótesis de valor explícita. Para formularla como afirmación falsable, ¿cuál de estas dos captura mejor lo que usted cree que va a pasar, o lo diría distinto: (a) "Si centralizamos la solicitud de recolección en una sola app, los clientes dejarán de usar llamada/WhatsApp/correo porque es más rápido y confiable que esperar respuesta manual", o (b) "El problema no es solo centralizar el canal, sino que el cliente confíe en que lo que pide en la app realmente se cumple (confirmación y recolección a tiempo), y por eso deja de llamar"? ¿O hay una tercera formulación que refleje mejor su apuesta?
**R:** Elige (b), sin dudarlo, y aclara que (a) es lo que habría contestado hace tres meses — suena bien pero si fuera cierto el problema se resolvería con un formulario de Google. Conecta esto con lo que él mismo escribió en §2 del brief: que si el equipo de recolección sigue desorganizado y los clientes se siguen quejando, es un fracaso total — eso es el corazón del asunto. El cliente no llama por falta de dónde escribir; llama porque no confía, porque la última vez le dijeron que sí y no pasó.

Formulación textual de la hipótesis, en sus propias palabras (transcripción literal, no parafraseada):

> "El cliente deja de llamar cuando la app le cumple. Nuestra apuesta es que si la solicitud recibe una confirmación firme y esa recolección efectivamente ocurre en la fecha y hora confirmada, el cliente deja de usar teléfono, WhatsApp y correo — no porque la app sea más cómoda, sino porque ya no necesita perseguirnos. Y eso solo es posible si detrás la programación de camiones y conductores es real y se cumple."

**Falsador declarado (el elemento más importante de la respuesta):** el indicador de refutación no es la adopción sino el **volumen de llamadas de seguimiento** ("¿sí van a venir?"). Criterio explícito del cliente: si construyen la app, la gente la usa, y aun así la gente sigue llamando a confirmar, la hipótesis está muerta — no importa que el 60% esté usando la app, significaría que centralizaron el canal sin arreglar nada.

**Riesgo asumido a conciencia (no descuido):** la app puede empeorar la situación si la parte de operaciones no funciona. Hoy los incumplimientos se pierden en un WhatsApp y nadie lleva la cuenta; con la app, cada promesa rota queda registrada con fecha, hora y estado en rojo, visible para el cliente — "estaríamos documentando nuestro propio fracaso con mucho detalle". Por eso el NPS de 85% es alto a propósito: si la operación no cambia, ese número se desploma y será evidente.

**Consecuencia de priorización:** el prototipo le importa más por el lado del Analista de Operaciones que por el del cliente — "la pantalla bonita del cliente la vende cualquiera"; lo que realmente se está apostando es que la programación automática sea buena y que el equipo la respete en vez de volver al Excel. Esto refuerza la priorización ya dada en Q1.

**Nota para §7 (pendiente de abordar ahí):** el gatekeeper del brief mide adopción (60%) y NPS (>85%), pero el verdadero falsador que el cliente acaba de declarar es el volumen de llamadas de seguimiento — un prototipo de 3 semanas de camino feliz no puede medir eso con datos reales, así que el gatekeeper del prototipo tendrá que ser un proxy. Queda pendiente de hacer explícito con el cliente al llegar a §7.

### Q6 · área: §4 — Poder de decisión de los stakeholders
**P:** El brief ya declara el interés/expectativa de cada stakeholder (Gerente General, Gerente de Operaciones, Analistas de Operaciones, Conductores, Usuarios/clientes), pero no su poder de decisión. Concretamente para el prototipo de estas 3 semanas: si hay un desacuerdo sobre alcance o una decisión de último momento, ¿quién tiene la última palabra? ¿Es usted como Gerente General, o delega esa decisión operativa en el Gerente de Operaciones? Y dado lo que acaba de contarme sobre priorizar el flujo del Analista de Operaciones, ¿ese rol tiene poder de veto sobre cómo se comporta la programación automática, o solo la opera una vez definida?
**R:** Corrección de dato: el humano **no es el Gerente General** — su rol es **Analista de Negocios**, y para estas tres semanas es la contraparte única del interviewer/prototipador. Pide explícitamente no consultar al Gerente General ni al Gerente de Operaciones para resolver "¿esto entra o no entra?" — solo a él, para evitar recibir tres respuestas distintas y perder días.

**Mapa de decisión:**
- **Analista de Negocios (el entrevistado):** última palabra sobre el alcance del prototipo.
- **Gerente General:** decide todo lo que toque presupuesto (45K) o plazo del proyecto completo (6 meses). Ni el Analista de Negocios ni el prototipador lo deciden; se escala.
- **Gerente de Operaciones:** decide todo lo que cambie cómo trabaja el equipo de recolección en la vida real — turnos, cómo se asignan camiones, qué se le puede exigir a un conductor. El Analista de Negocios no puede cambiarle la operación desde un prototipo.
- **Conductores y clientes:** no deciden nada en estas tres semanas; son **observados, no consultados**. Si un conductor señala algo (p. ej. pantalla incómoda), se anota para el MVP y se sigue.

**Protocolo de desbloqueo (regla operativa para el prototipado):** el Analista de Negocios se compromete a responder en **menos de 4 horas hábiles**. Si vence el plazo sin respuesta, el constructor está autorizado a tomar la decisión que **menos alcance agregue** y seguir; se lo cuenta después y el Analista de Negocios asume esa decisión.

**Regla de escalamiento:** el constructor no escala directo a los gerentes; avisa al Analista de Negocios y es él quien escala (a Gerente General si toca presupuesto/plazo, a Gerente de Operaciones si toca la operación real).

**Veto desdoblado del Analista de Operaciones (distinción fina):**
- Sobre **cómo funciona el algoritmo** de asignación: no tiene veto. Esa regla la define el equipo del prototipo ahora, y en el MVP la decide el Gerente de Operaciones. Darle veto a los analistas sobre la lógica llevaría a que cada uno pida que el sistema replique su Excel actual — "automatizar el desorden actual", justo lo que se busca romper.
- Sobre si la programación es **utilizable**: sí tiene un veto de hecho. Si el analista mira la programación propuesta y dice "esto no lo puedo confirmar, en la práctica no funciona", es una alerta seria que no se ignora — pero no la resuelve él solo: se lo comunica al Analista de Negocios, quien lo lleva al Gerente de Operaciones, y este decide si se cambia la regla o si el analista se adapta.

Frase textual del cliente: "el analista no diseña la programación, pero si el analista no la puede confirmar, la programación está mal." Traza el vínculo explícito con la hipótesis de valor (Q5/§2): si un analista empieza a reprogramar todo manualmente por desconfianza en lo que propone el sistema, "volvimos al punto de partida" — es el mismo falsador de la hipótesis (el volumen de llamadas/reprogramaciones de seguimiento) visto desde el lado de la operación.

### Q7 · área: §7 — Método de medición del Gatekeeper (del prototipo, no del proyecto)
**P:** El brief da métrica y umbral (60% de adopción, NPS > 85%) pero no dice cómo ni sobre qué universo se miden — y usted mismo acaba de decir que el verdadero indicador de que la hipótesis funciona es el volumen de llamadas de seguimiento, no la adopción. Un prototipo de 3 semanas de camino feliz no genera datos reales de uso ni llamadas reales que medir. Entonces, para el gatekeeper de este prototipo específicamente (no del proyecto completo a 6 meses): ¿qué necesita ver funcionando en la demo del comité para considerar que el prototipo "pasó"? Por ejemplo: ¿le basta con que el camino feliz completo (cliente pide → analista confirma en 5 min → conductor/camión queda asignado sin cruces → cliente ve el estado avanzar) se ejecute sin errores frente a él, o hay algo más específico —como cierto número de escenarios de prueba, o que el Gerente de Operaciones lo valide en vivo— que use como criterio de "esto sí sirve"?
**R:** Confirma la separación de horizontes: adopción 60% y NPS > 85% no se pueden medir en tres semanas y no va a fingir que sí — son del proyecto a 6 meses, con clientes reales. Para el prototipo da **cuatro criterios conjuntivos**: los cuatro se cumplen o el prototipo no pasa.

1. **Camino feliz completo, en vivo, sin trampas:** cliente pide, se confirma en los 5 minutos, quedan asignados conductor y camión sin cruces, y el cliente ve el estado avanzar con la convención de colores — de principio a fin, delante del comité, con la aplicación funcionando de verdad. Nada de mostrar una imagen de cómo se vería ni de saltarse un paso porque falla. Si hay que explicar por qué algo no se puede mostrar, ya no pasó.

2. **Mínimo tres solicitudes, no una:** en la misma franja horaria, con materiales y tamaños distintos, para que se vea que a cada una le corresponde el camión adecuado (regla dura 2 de Q3) y que ningún conductor queda con citas cruzadas (regla dura 1 de Q3). Este es el momento de la demo que le importa al Gerente de Operaciones, no la pantalla del cliente.

3. **Un Analista de Operaciones real lo opera en frío (el de mayor peso, proxy explícito de la hipótesis de §2):** se sienta a un analista real, sin entrenamiento previo, frente a la pantalla, y se le pide revisar y confirmar la programación. Deben pasar dos cosas: que entienda qué está viendo sin que nadie le explique, y que confirme **sin querer reprogramar**. Si el primer impulso del analista es cambiar la programación, el prototipo falló aunque el software funcione perfecto — "es el mejor proxy que tengo de la hipótesis que discutimos: si quien opera no confía en lo que propone el sistema, el cliente tampoco va a confiar, y volvemos al Excel". Lo declara como el criterio que "de verdad le quita el sueño".

4. **El Gerente de Operaciones lo dice en voz alta:** al final de la demo se le pregunta directamente si esto le sirve para organizar su operación; necesita un **sí explícito** — "está bonito" no cuenta como sí. Razón: él tiene que vivir con esto, y si no se compromete ahí, el MVP arranca sin dueño real.

### Q8 · área: §6 — Convención de colores y estado de "retrasado"
**P:** El brief menciona el flujo de estados que ve el cliente (solicitud → confirmación de solicitud → confirmación de recolección → inicio → recolección → cierre) y usted mencionó varias veces una "convención de colores" para representarlo, pero no la describió en detalle. Para que el prototipo la muestre bien en la demo: ¿ya tiene en mente qué color corresponde a cada estado (por ejemplo, algo tipo semáforo: gris/amarillo mientras se procesa, verde cuando está confirmado, rojo si algo se incumple o se retrasa), o prefiere que le proponga una convención simple de 3-4 colores y usted la valida? Y puntualmente: ¿hay un estado de "incumplido" o "retrasado" que deba verse en rojo, dado lo que me contó sobre que cada promesa rota queda ahora registrada y visible?
**R:** **Nota honesta de proceso:** la primera mitad de esta pregunta era redundante — la convención de colores ya estaba completa en el brief (client_brief.md, texto correspondiente a la descripción del flujo del cliente), pero `_prototype/document_extract.md` no la capturó (no aparece en su tabla de cobertura ni en sus extractos por área), así que no estaba disponible para el interviewer al formular la pregunta. Causa raíz: falla de la etapa de ingesta, no de esta entrevista. Cita literal del brief, para que el material quede en la cadena (el writer lee log + extracto, y el extracto no la tiene):

> "Ademas, debe tener una convencion de colores, Verde para realizado y gris claro para pendiente. Ademas cuando la recoleccion se llevo a cabo exitosamente utiliza el color verde, pero si se llevo a cabo de forma parcial utiliza el amarillo y si no se pudo llevar a cabo utiliza el color rojo. El cierre utilizará esta misma convencion."
> — client_brief.md (sección "5. Cómo lo usarían, paso a paso", descripción del flujo del cliente)

> "Ejemplo cuando el cliente solicita la recoleccion el flujo muestra Solicitud en color verde y abajo muestra la fecha y hora de realizacion de la solicitud."
> — client_brief.md (misma sección)

El cliente confirma esa convención tal cual y pide no gastar preguntas de su presupuesto en material ya escrito.

**Respuesta a la parte nueva (estado de "retrasado"):** distingue dos cosas. El rojo/amarillo que ya existe en su convención corresponde a un **hecho reportado por una persona** — el conductor reporta que la recolección fue parcial (amarillo) o que no pudo recoger (rojo) — y eso sí entra en el prototipo. Lo que el interviewer preguntaba es distinto: un estado de "retrasado" **calculado automáticamente por el sistema**, comparando la hora confirmada contra el reloj. Eso NO se construye ahora.

Razón declarada (no es por ahorrar esfuerzo): un retraso automático obliga a definir tolerancia en minutos, si depende del tipo de material, y qué pasa si el camión va en camino pero demorado — son reglas de operación real, competencia del **Gerente de Operaciones** (coherente con el mapa de decisión de §4/Q6), no del Analista de Negocios.

**Criterio de demo:** el camino feliz recorre **solo gris → verde**; los seis estados avanzan y todo termina en verde. Si aparece rojo en la demo del comité, es señal de que algo se rompió, no una funcionalidad que se esté demostrando. Amarillo y rojo quedan funcionales (por el reporte del conductor) pero fuera del recorrido principal de la demo — mostrables aparte si alguien pregunta.

**Aplazado a MVP:** cálculo automático de retraso, con su definición de tolerancia por tipo de material y tratamiento de camión demorado en ruta, a cargo del Gerente de Operaciones.

La preocupación por que las promesas rotas queden registradas y visibles (mencionada en Q5/§2) sigue vigente pero como asunto del producto en operación real — no se reabre ni se resuelve en el prototipo.

**Nota de método para el resto de la entrevista:** de aquí en adelante, contrastar cada pregunta candidata contra `client_brief.md` directamente, además del extracto, antes de formularla — el extracto demostró estar incompleto en al menos este punto.

### Q9 · área: §6 — Canales de notificación (reales vs. simulados)
**P:** El brief dice que el cliente recibe confirmaciones por email, WhatsApp o notificación push. Integrar de verdad WhatsApp Business API o push notifications reales puede comerse días del presupuesto de 15 hábiles que no tiene previstos para eso. Para el prototipo: ¿le sirve que esas notificaciones se simulen dentro de la propia app (por ejemplo, un panel o bandeja "notificaciones" visible en pantalla, sin salir realmente por email/WhatsApp/push), o es importante para la demo que al menos un canal salga de verdad —por ejemplo un correo real— aunque sea con un proveedor simple?
**R:** Quiere un canal de verdad, y explica por qué no es capricho: la apuesta central (§2/Q5) es que el cliente deja de perseguir información porque se le avisa sin que tenga que preguntar. Si la notificación vive solo dentro de la app, el cliente sigue teniendo que entrar a buscarla — es más cómodo que llamar, pero es la misma dinámica de persecución. Si en la demo solo hay una bandeja interna, el Gerente General preguntará "¿y al cliente cómo le llega?", y "abriendo la app" no es la respuesta que quiere dar en esa sala.

**Decisión puntual:** el correo electrónico sale de verdad, un solo canal. Proveedor más simple que se encuentre, sin plantillas, texto plano si hace falta. Requisito de demo: pedir una recolección desde su teléfono durante la demo y que el correo llegue en vivo a la bandeja de alguien del comité, mientras están sentados ahí — "ese momento vale más que veinte diapositivas".

**Requisito de contenido del correo (verificable, no es detalle de copy):** debe traer la **fecha y hora confirmadas**, no un acuse genérico tipo "su solicitud fue recibida". Si el mensaje obliga a entrar a la app para ver el dato, se reproduce el problema original que el proyecto vino a resolver.

**Techo de esfuerzo declarado (caso concreto del protocolo de desbloqueo de §4/Q6):** si el correo real cuesta más de un día de trabajo, se detiene la construcción y se le avisa.

**WhatsApp y push:** simulados, dentro de la bandeja de notificaciones interna de la app, y **marcados visiblemente como simulados** — mismo tratamiento que los botones de Gmail/Apple de A1 (Q4): "enseñar el plano, no una fachada de cartón". Razón: WhatsApp Business tiene trámite de aprobación propio que no controla, y no lo va a meter en tres semanas.

**Criterio general declarado para no ser consultado caso por caso (el elemento más importante de esta respuesta — regla de decisión autónoma para el resto del prototipo):**
- **Simular** todo lo que sea trámite externo fuera del control del equipo (WhatsApp Business, cuentas de desarrollador, OAuth de Google/Apple) — ahí el tiempo no depende de ellos y se lo pueden "robar entero".
- **Construir de verdad** lo que demuestre la hipótesis. Avisarle al cliente sin que pregunte no es un canal de entrega más: es literalmente la hipótesis (§2).

### Q10 · área: §6 — Tipos de camión y tabla de correspondencia material/tamaño
**P:** Para la regla dura de que el tipo de camión debe corresponder al material y tamaño (de la pregunta 3), necesito los tres tipos de camión concretos y su tabla de correspondencia. El brief menciona materiales como cartón, vidrio "u otro", y tamaños sin especificar categorías. Para el prototipo, ¿le sirve algo simple como: Camión Tipo A = carga pequeña/mixta, Tipo B = vidrio/frágil, Tipo C = carga grande/voluminosa; con tamaño en 2-3 categorías (pequeño/mediano/grande)? ¿O ya tiene en mente los tres tipos y su tabla, y prefiere dármelos usted para no inventar una clasificación que no corresponda a su operación real?
**R:** No tiene la tabla y no la va a inventar: es exactamente lo que dijo en Q6 — las reglas de cómo se despacha un camión son del Gerente de Operaciones, no suyas. Si él arma esa tabla desde su escritorio, el equipo de recolección la verá en la demo y dirá "eso no es así", perdiendo justo el criterio 4 del gatekeeper (compromiso verbal del Gerente de Operaciones).

**Compromiso con fecha:** consigue la tabla real hablando con el Gerente de Operaciones, con entrega para el **día hábil 3**. Mientras tanto se arranca con una tabla **provisional, marcada explícitamente como tal** en el código o donde corresponda, para que sea localizable y reemplazable — no debe llegar el día 8 con la provisional todavía puesta. Si el día 3 no llega la tabla real, se le avisa y él escala.

**Corrección sustantiva al esquema propuesto por el interviewer (defecto de diseño, no matiz):** el esquema propuesto colapsaba material y tamaño en una sola etiqueta de tipo de camión ("Tipo B = vidrio/frágil", "Tipo C = carga grande"), lo que genera solapamiento y ambigüedad — un vidrio grande cabría en Tipo B y en Tipo C a la vez, y el sistema no podría desambiguar. Ejemplo dado: vidrio pequeño de una casa vs. vidrio de gran volumen de un restaurante no son el mismo camión.

**Estructura confirmada (esto sí lo decide él, porque es estructura, no operación):** una **rejilla material × tamaño** — 3 materiales (cartón, vidrio, otro) × 3 tamaños = **9 filas**, cada una apunta a un tipo de camión. Varias filas pueden apuntar al mismo camión (se esperan 3-4 tipos de camión, no 9); ninguna celda queda ambigua. Construir esperando esta forma para que el día 3 solo se llenen las celdas con los datos reales.

**Distinción de competencias aplicada (refina el mapa de §4/Q6):** la **estructura** de la tabla (rejilla material × tamaño) la decide el Analista de Negocios porque es diseño; el **contenido** —qué vehículos existen realmente y qué carga cada uno— es del Gerente de Operaciones porque es operación real.

**Redacción de los tamaños cara al cliente (decisión suya):** no usar "pequeño/mediano/grande" en abstracto —no significa nada para alguien en su apartamento con cajas—, sino referencias físicas comprensibles: "cabe en el baúl de un carro" / "necesita una camioneta" / "necesita un camión". Los tamaños tienen entonces dos representaciones: la etiqueta interna del eje de la rejilla y el texto que ve el cliente.

### Q11 · área: §6 — Cuentas de staff para la demo (Administrador dentro o fuera del prototipo)
**P:** El brief dice que el Administrador es quien registra en la aplicación a los conductores, analistas y gerentes. Usted priorizó el flujo del cliente y del Analista de Operaciones, y dejó los dashboards gerenciales como sacrificables — pero no mencionó al Administrador. Para el prototipo: ¿el flujo de creación de usuarios por el Administrador entra en el camino feliz que se construye, o para la demo simplemente precargamos en los datos de prueba al analista, el o los conductores y sus usuarios/contraseñas ya creados (como hicimos con conductores y camiones en la regla dura 3), sin construir la pantalla del Administrador?
**R:** Precargarlos; la pantalla del Administrador no entra. No lo mencionó antes porque para él nunca estuvo en discusión, pero reconoce que estuvo bien preguntarlo en vez de asumirlo.

**Criterio aplicado (generaliza el mismo razonamiento de Q3 sobre camiones/conductores):** el Administrador es un rol de **puesta en marcha**, no parte del recorrido que se quiere demostrar. Nadie en el comité se va a emocionar viendo un formulario de crear usuarios —lo ha visto mil veces en cualquier sistema—; lo que no ha visto es que un pedido de recolección entre y salga programado solo.

**Decisión:** analista, conductores y gerentes ya creados, con credenciales listas antes de la demo; cada rol debe poder entrar con su usuario y ver su pantalla.

**Requisito de calidad de los datos de demo (verificable, no es preferencia estética):** datos realistas — nombres que suenen a personas, correos con el dominio de la empresa, placas de camión con formato colombiano real. Explícitamente prohibido: "analista1", "conductor_test", "prueba@prueba.com". Razón: los datos de juguete restan seriedad delante del Gerente General y cuestan lo mismo que hacerlos bien.

**Requisito de volumen de los datos (dependencia cruzada explícita con la regla dura 1 de Q3 y el criterio 2 del gatekeeper de Q7):** el juego de datos debe tener suficientes conductores y camiones para sostener simultáneamente "sin cruces de horario" y "tres solicitudes en la misma franja con materiales y tamaños distintos". Modo de fallo advertido: con dos conductores y tres solicitudes simultáneas, la demo se cae por falta de datos, no por defecto del software — hay que dimensionar el juego de datos para evitarlo.

**Manejo en la demo:** si alguien pregunta quién crea a los conductores, lo responde él de palabra — "existe el rol, está descrito, se construye en el MVP". Lo que le costaría caro es haber gastado dos días de los quince en una pantalla que nadie va a mirar.

**Aplazado a MVP:** pantalla y flujo de administración de usuarios (rol Administrador).

### Q12 · área: cierre de la entrevista
**P:** Con 11 preguntas (de las 20-25 acordadas) considero que el camino feliz del cliente y del Analista de Operaciones —lo que usted marcó como el corazón del prototipo— quedó cubierto en profundidad, junto con las tres ambigüedades del brief resueltas con decisiones suyas. Lo único sin detallar son los dashboards gerenciales, que usted mismo dejó como sacrificables y "con datos de muestra" si alcanza el tiempo. ¿Está de acuerdo en que cerremos aquí la entrevista, dejando los dashboards como hueco declarado (no como pregunta pendiente), o prefiere que profundice en algo más antes de cerrar?
**R:** "si cerremos las preguntas" — cierre confirmado por el humano.

## Cierre

- **Motivo de cierre:** Suficiente para el camino feliz del generador. El humano confirmó explícitamente el cierre en Q12 tras 11 preguntas de contenido (de las 20-25 acordadas en el timebox de Q1); no se agotó el timebox, se cerró por suficiencia declarada por el propio entrevistado.

- **Balance de cobertura de §1–§10:**
  - §1 (objetivo y contexto): cubierta por el documento — no repreguntada.
  - §2 (hipótesis de valor central): cubierta por la entrevista (Q5) — hipótesis falsable en palabras del cliente, con falsador declarado (volumen de llamadas de seguimiento, no adopción).
  - §3 (tipo de prototipo dominante): n/a — no le corresponde al cliente, lo deduce el Descubridor.
  - §4 (stakeholders / poder de decisión): cubierta por la entrevista (Q6) — mapa de decisión, protocolo de desbloqueo (4h hábiles), regla de escalamiento, veto desdoblado del Analista de Operaciones.
  - §5 (actores): cubierta por el documento — no repreguntada.
  - §6 (camino feliz + medio por actor): cubierta en profundidad por la entrevista (Q2, Q3, Q4, Q8, Q9, Q10, Q11) — ventana única de confirmación (5 min), algoritmo de asignación por zona con tres reglas duras, registro sin validación real + botones inertes Gmail/Apple, convención de colores (confirmada, ya estaba en el brief), canales de notificación (correo real + WhatsApp/push simulados), tabla camión×material×tamaño (estructura confirmada, contenido pendiente al día hábil 3 — ver huecos), cuentas de staff precargadas sin pantalla de Administrador.
  - §7 (Gatekeeper): cubierta por la entrevista (Q7) — cuatro criterios conjuntivos del prototipo, distintos de la métrica de adopción/NPS del proyecto a 6 meses.
  - §8 (timebox): cubierta por la entrevista (Q1) — timebox de la entrevista y del prototipo (3 semanas / 15 días hábiles, feature freeze día hábil 10), acordado antes del bucle.
  - §9 (exclusiones): cubierta por el documento — no repreguntada; su conflicto aparente con §6 (A1) quedó resuelto en Q4.
  - §10 (split por audiencia): n/a — el documento no plantea necesidad de artefactos segmentados por audiencia.
  - A1, A2, A3 (ambigüedades del extracto): las tres resueltas con decisiones propias del cliente (Q4, Q2, Q3 respectivamente).

- **Huecos declarados:**
  1. **Dashboards del Gerente General y del Gerente de Operaciones (§6, parte no priorizada):** no se preguntó en profundidad por decisión explícita del humano (Q1) — quedan como sacrificables para el prototipo, construibles "si alcanza" y con datos de muestra. Es un hueco consciente, no una omisión: el humano priorizó expresamente el flujo del cliente y del Analista de Operaciones sobre estos dashboards.
  2. **Contenido real de la tabla camión × material × tamaño (§6 / Q10):** la estructura (rejilla 3×3, material × tamaño) quedó confirmada y cerrada, pero el contenido de las celdas —qué tipos de camión existen realmente y qué carga cada uno— depende de que el Analista de Negocios lo obtenga del Gerente de Operaciones, comprometido para el día hábil 3. Hasta entonces se construye con una tabla provisional marcada como tal.

- **Incidente de proceso (constancia para el `onboarding-writer`):** `_prototype/document_extract.md` resultó **incompleto** — no capturó la convención de colores que sí estaba en el brief (`_context/client_brief.md`, líneas 56 y 58, sección "5. Cómo lo usarían, paso a paso"), lo que llevó a una pregunta redundante (Q8) que el propio cliente señaló como gasto innecesario de su presupuesto de preguntas. La causa raíz es de la etapa de ingesta (`onboarding-reader`), no de esta entrevista. **Recomendación explícita para el writer:** al redactar `discovery.md`, contrastar también contra `_context/client_brief.md` directamente y no apoyarse únicamente en `document_extract.md` y en este log, para no perder o duplicar material que el extracto no haya capturado correctamente.
