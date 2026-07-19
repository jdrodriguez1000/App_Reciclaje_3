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

## Cierre

<!-- Rellenar solo al cerrar la entrevista (Estado: cerrada). -->

- **Motivo de cierre:** <pendiente>
- **Huecos declarados:** <pendiente>
