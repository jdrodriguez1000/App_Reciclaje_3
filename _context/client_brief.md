

# Qué quiero construir — <nombre-del-proyecto>

- **Quién escribe esto:** Jota D - Analista de Negocios
- **Fecha:** 2026-07-19


---

## 1. Qué problema quiero resolver

La empresa Recicladora Oriente Verde, quiere crear una aplicacion para que sus clientes soliciten la recoleccion del reciclaje a traves de esa aplicacion y asi despues ellos organizar el despacho de camiones y conductores para recolectar ese material.  Hoy en dia, el servicio se presta a traves de una llamada telefonica, whastapp o por medio de un correo electronico.  Esto no es centralizado y genera desorden, a veces no se leen los correos electronicos o los mensajes de WhastApp a tiempo, en otras ocasiones cuando se recibe una llamada telefonica y debido a la presion del cliente se le dice que se pasará hoy por el reciclaje pero ya los camiones de recoleccion no pueden pasar por ese material.  ESto los esta llevando a tener problemas con sus clientes y con los equipos de recoleccion de material.


## 2. Cómo sabría que esto funcionó
El proyecto será existoso si el 60% de mis clientes actuales utilizan la aplicacion para solicitar sus pedidos de recoleccion de datos. Pero ademas quiero tener un NPS superior al 85%.

Tambien si logramos que el equipo de recoleccion de material, logra trabajar con esta aplicacion y organizar los camiones y conductores que realizan la recoleccion.
Si el equipo de recoleccion sigue desorganizado, utilizando Excel u otras aplicaciones y como consecuencia de eso los clientes se siguen quejando, esto seria un fracaso total.

## 3. Quién tiene interés en esto

1. EL primer interesado es el Gerente General de la compañia, el es el patrocinador principal de la solucion y quien actualmente esta soportando todas las quejas de sus clientes. El espera que los clientes usen la aplicacion, pero sobre todo que el numero de quejas disminuya a casi cero por no recoleccion de material segun lo pactado.
2. El Gerente de Operaciones, es el segundo interesado principal, lo que mas espera es tener orden y control total del proceso por medio de la solucion. Esto implica que se pueda recolectar el material segun lo organizado por la aplicacion.
3. Los Analistas de Operaciones: Son los encargados de asignar conductores y camiones para la recoleccion del material segun la disponibilidad de estos. Es importante que la aplicacion les entregue la mejor planeacion posible o el mejor momento de recoleccion segun como se van realizando los pedidos de recolecion de los clientes.
4. Los conductores de vehiculos quienes de forma organizada veran la programacion de sus recorridos, pudiendo de esta forma poder recolectar el material sin necesidad de realizar cambios de ultimo momento o sabiendo siempre que estan cumpliendo con las expectativas de los clientes.
5. Los usuarios (clientes) quienes utilizan la aplicacion para realizar la solicitud de pedido de recoleccion de material reciclado. Ellos esperan que la empresa recoja el material segun lo programado por la aplicacion.


## 4. Quién va a usarlo
1. El usuario (cliente) es el principal usuario, es quien solicita por medio de la solucion la recoleccion del material reciclado.
2. El Analista de Operaciones: Es quien recibe las solicitudes de recoleccion de material realizadas por los usuario y verifica y despues confirma la programacion entregada por la aplicacion para la recoleccion del material. Si no esta de acuerdo con la programacion entregada por la aplicacion puede proponer una nueva fecha / hora de recoleccion.
3. El Conductor quien ingresa a la aplicacion para visualizar las recolecciones que debe realizar segun el recorrido. Cada vez que realiza un recorrido confirma su recoleccion y en caso contrario informa que no lo pudo hacer y el motivo.
4. El Gerente de Operaciones: Quien ingresa a la aplicacion para visualizar el plan de trabajo de recoleccion de material reciclado, ademas ve indicadores como el porcentaje de recoleccion a tiempo, los principales motivos de no recoleccion, entre otros para que pueda tomar decisiones para futuros cambios en sus procedimientos y procesos.
5. El Gerente General, quien ingresa a la aplicacion para saber el nivel de NPS, el porcentaje / numero de usuarios que esta utilizando la aplicacion, ademas tambien puede ver otros KPIS que indiquen si la aplicacion esta cumpliendo con las expectativas de la empresa.
6. El Administrador: Es un usuario tecnico (sistemas) quien registra en la aplicacion a usuarios que no son clientes de la empresa. Por ejemplo registra conductores, analistas, a los gerentes. En general es quien administra la aplicacion y es responsable de saber que esta siempre disponible.



## 5. Cómo lo usarían, paso a paso

1. El usuario (cliente): Este se registra en la aplicacion, este registro es por email con validacion de correo o puede ser utilizando sus corros de gmail o de apple.  Despues de registrarse y confirmar su correo, el siguiente paso es registar los lugares donde quiere que recolecten el material, el usuario puede registar un solo sitio o varios sitios, por ejemplo puede registrar como sitio 1 con un nombre y su direccion, por ejemplo Apartamento, ademas puede registrar dos o mas sitios. Despues de Registrar los sitios puede solicitar la recogida del material.  Para esto el usaurio debe primero informar el material que se va recolectar como carton, vidrio u otro y el tamaño, esto es importante para saber que tipo de camion se envia para esa recoleccion, ademas registra una fecha y hora de recoleccion y por ultimo confirma la solicitud de pedido.

Despues de confirmar la solicitud en la pantalla de la aplicacion se le informará que recibira un email, una notificacion push o un mensaje por WhatsApp que le confirma la solicitud de pedido, pero se le dice qeu está en proceso de validacion la fecha y hora solicitada.  Al cabo de 5 minutos recibirá un email, un mensaje de Whastapp o una notificacion push donde se le informa la fecha y hora confirmada para la recoleccion, ademas en la pantalla de la aplicacion puede ver esta informacion.


Por pantalla este usuario puede ir observando el estado de la solicitud de recoleccion como un flujo, ejemplo:
1.1. Solicitud con fecha y hora. 
1.2. Confirmacion solicitud - Fecha y hora.
1.3. Confirmacino de recoleccion - Fecha - hora.
1.4. Inicio de recoleccion - Fecha y hora.
1.5. Recoleccion - Fecha y hora.
1.6. Cierre Recoleccion - Fecha - hora.

Ademas, debe tener una convencion de colores, Verde para realizado y gris claro para pendiente. Ademas cuando la recoleccion se llevo a cabo exitosamente utiliza el color verde, pero si se llevo a cabo de forma parcial utiliza el amarillo y si no se pudo llevar a cabo utiliza el color rojo.  El cierre utilizará esta misma convencion.

Ejemplo cuando el cliente solicita la recoleccion el flujo muestra Solicitud en color verde y abajo muestra la fecha y hora de realizacion de la solicitud.

Lo usa principalmente en una app en su telefono movil.

2. El usuario Analista de OPeraciones: Ingresa a la aplicacion por medio de usuario y contraseeña, su labor principal es revisar la programacion entregada por la aplicacion y confirmarla.  Si este usuario no confirma en un plazo maximo de 1 hora, la aplicacion asume la confirmacion. Ese usuario es el unico que puede reprogramar una recoleccion pero solo lo puede hacer antes de la cofrimacion de fecha y hora, despues de eso ya no la puede cambiar. Lo usa principalmente en una web en su equipo de computo.

3. El conductor ingresa a la aplicacion por medio de usuario y contraseña, y conoce la programación de las recolecciones qeu debe tener en su turno para ese dia. El conductor cada vez que recoge informacion lo notifica a traves de la aplicacion, sea que fue exitosa o que su recoleccion fue parcial o no fue exitosa. Lo usa principalmente en una app en su telefono movil.

4. El Gerente de operaciones ingresa por medio de usuario y contraseña, cada vez que ingresa observa un dashboard con los principales KPIs de su rol. Lo usa principalmente en una web en su equipo de computo.

5. El gerente general  ingresa por medio de usuario y contraseña, cada vez que ingresa observa un dashboard con los principales KPIs de su rol. Lo usa principalmente en una web en su equipo de computo.

6. El administrdor ingresa por medio de un usuario y contraseña, cada vez que ingresa entra a un tablero de control que le permite registrar, inactivar usuarios, asignar segun el rol a los usuarios, tambien valida el estado de la aplicacion que no este teniendo problemas. Lo usa principalmente en una web en su equipo de computo.


## 6. Cómo mediríamos el éxito

1. Que el 60% de los clientes utilice la aplicacion para realizar la solicitud de pedidos de recoleccion de material.
2. Que el NPS sea superior al 85%.
3. Que no se utilicen otras aplicaciones para organizar la recogida de material reciclado.

## 7. Plazos y restricciones


- **¿Para cuándo lo necesitas?** 
  La aplicacion se debe construir en un plazo maximo de 6 meses.

- **Presupuesto o límite de esfuerzo:** <si aplica>
El presupuesto es 45K USD.

- **Restricciones innegociables:** 
Politica de seguridad de datos de los clientes.

## 8. Qué NO quiero que se haga ahora
1. Validacion de correo electronico.
2. Tampoco validacion de correo con gmail o con apple
3. Se debe seguir el camino feliz.

## 9. Referencias, ideas previas y material existente
No se tiene referencia de alguna aplicacion.

## 10. Dudas que tengo yo
La duda que tengo es como la aplicaicon asigna la programacion para los conductores, utiliza algun algoritmo de optimizacion de rutas o cual otro puede utilizar.