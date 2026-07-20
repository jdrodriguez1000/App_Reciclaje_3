# Entrevista de descubrimiento (log crudo) — ReciclApp

## Meta

- **Proyecto:** ReciclApp <!-- FUENTE: _context/project.yaml (project.name) -->
- **Entrevistado:** <por confirmar con el humano>
- **Entrevistador:** onboarding-interviewer
- **Inicio:** 2026-07-19
- **Timebox acordado:** Entrevista: 45 min / 20-25 preguntas (medir por preguntas, no reloj); si a la P25 quedan vacíos importantes, se anotan como supuestos marcados para una segunda ronda corta, sin alargar esta sesión. Prototipo: 3 semanas calendario (15 días hábiles), arranca el lunes siguiente al cierre de esta entrevista; feature freeze al cierre del día hábil 10 (fin semana 2) — los 5 días restantes son solo estabilización; si el alcance no cabe, se avisa el día 7-8, no el día 14.
- **Estado:** en curso
- **Sección en curso:** §6 (camino feliz — flujo cliente/generador y Analista de Operaciones)
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

## Cierre

<!-- Rellenar solo al cerrar la entrevista (Estado: cerrada). -->

- **Motivo de cierre:** <pendiente>
- **Huecos declarados:** <pendiente>
