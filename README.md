## ESTUDIANTE: ALEXA AZUCENA ESPINAL ROSARIO. 
## ASIGNATURA: BASE DE DATOS. 
## CRUSO: 5TO B DE INFROMATICA.

## ✨ Documentación sobre Triggers en Bases de Datos
Bienvenidos a esta documentación, donde aprenderemos todo lo relacionado con los Triggers en bases de datos: qué son, para qué sirven, cómo se crean, y por qué son tan importantes en el manejo automatizado de información.

Aquí exploraremos sus características, estructura, tipos, y hasta ejemplos reales con instrucciones paso a paso, que te ayudarán a comprender su funcionamiento de forma clara y práctica.

## ¡Vamos a prestar mucha atención!
Esta información te será muy útil si estás estudiando o trabajando con bases de datos y quieres mejorar la automatización y el control de tus sistemas.

primero debemos saber 
## 1. ¿Qué es un Trigger?
Un Trigger (o disparador) es una función automática dentro de una base de datos que se activa cuando ocurre una acción específica, como agregar, modificar o eliminar datos en una tabla.

Es como una alarma que se dispara cuando pasa algo y realiza una tarea sin que el usuario tenga que hacer nada más.

## 2. ¿Para qué sirve un Trigger?

Sirve para:
- Automatizar tareas.
- Validar datos.
- Auditar cambios (llevar historial).
- Enviar notificaciones automáticas.
- Mantener la integridad entre tablas.

 **Ejemplo de uso:** registrar automáticamente en una tabla de auditoría cada vez que se agrega un nuevo empleado.

---
## 3. ¿Cuándo se puede usar un Trigger?

Puedes usar un Trigger cuando necesitas:
- Ejecutar acciones al modificar datos sin que el usuario lo haga directamente.
- Validar reglas complejas que no se pueden hacer solo con restricciones (`CHECK`, `NOT NULL`, etc.).
- Automatizar el control de versiones de datos.
- Crear logs internos sin usar la aplicación externa.

---

## 4. Estructura de un Trigger
 la estructura de un trigger en sql server es la siguiente:

CREATE TRIGGER trigger_insert_empleado
AFTER INSERT ON empleados
FOR EACH ROW
BEGIN
   INSERT INTO auditoria (accion, fecha)
   VALUES ('Nuevo empleado agregado', NOW());
END;

## tipos de trigger 

Los triggers se dividen según el momento en que se activan y el tipo de acción que los dispara. Los principales tipos son:

BEFORE INSERT: Se ejecuta antes de insertar un nuevo dato.

AFTER INSERT: Se ejecuta después de insertar un nuevo dato.

BEFORE UPDATE: Se ejecuta antes de actualizar un dato.

AFTER UPDATE: Se ejecuta después de actualizar un dato.

BEFORE DELETE: Se ejecuta antes de eliminar un dato.

AFTER DELETE: Se ejecuta después de eliminar un dato.

Cada tipo permite realizar acciones automáticas dependiendo del momento en que ocurre el cambio en la tabla.

## ¿Cuándo ejecuta su acción un Trigger?

Un Trigger se ejecuta automáticamente cuando ocurre el evento para el que fue configurado:

Cuando se inserta un nuevo registro.
Cuando se actualiza un dato.
Cuando se elimina un registro.

## Ejemplo:
Si tienes este trigger:

CREATE TRIGGER trigger_eliminar_producto
AFTER DELETE ON productos
FOR EACH ROW
BEGIN
   INSERT INTO auditoria (accion, fecha)
   VALUES ('Producto eliminado', NOW());
END;

  ## Este trigger se ejecutará justo después de que se elimine un producto en la tabla productos y guardará un registro en la tabla auditoria.


## Trigger en Marketing
En marketing, un trigger es un evento que activa una acción automática, como enviar un mensaje o hacer una oferta personalizada.

Estos triggers se usan en estrategias de automatización de marketing para mejorar la experiencia del cliente.

## Ejemplos:
Cuando un cliente abandona el carrito de compras → se envía un correo recordatorio.

Cuando un usuario se registra en una página → se envía un mensaje de bienvenida.

Si un cliente no compra durante 30 días → se envía una promoción especial.

Estos triggers permiten mantener contacto con los clientes en el momento justo, de forma automática.


## Cómo hacer un Trigger. 
Para crear un Trigger en una base de datos, debes seguir los siguientes pasos:

## Nota:
Crear un trigger en una base de datos es como enseñarle a la base de datos a reaccionar automáticamente cuando pasa algo (por ejemplo, cuando se agrega o borra un dato). Aquí te explico paso por paso cómo hacerlo, como si fuera un tutorial.

## Paso 1: Vamos a ir a sql sever: 

## Paso 2: Y crearemos una base de datos y una tabla  pero si ya tienes una creada y es la que vas a usar no tienes que crear la base de datos . 

## Y como creo una base de datos.
facil 
con este codigo crearemos nuestra base de datos.
CREATE DATABASE BD_TiendaAlexa;
GO
y le dan a ejecutar.

## Esta es mi tablas y base de datos BD_TiendaAlexa. 
![Trigger Marketing](img6.png)

asi se deberia ir viendo tu new guery. 

## Explicacion del codigo.

USE BD_TiendaAlexa;
Indica que se trabajará dentro de la base de datos llamada BD_TiendaAlexa.

Tabla Facturas
Se creó una tabla para almacenar información relacionada con ventas o facturas. Contiene los siguientes campos:

ID: Identificador único, clave primaria con incremento automático.

Descripcion: Nombre o detalle del producto o servicio.

Categoria: Tipo o clasificación del producto.

Cantidad: Número de unidades vendidas.

Precio_Unitario: Precio individual por unidad.

ITEBIS: Impuesto aplicado a la venta.

Descuento: Monto descontado de la venta.

Total_General: Monto total de la factura.

SELECT de la tabla Facturas
Consulta que muestra todos los datos almacenados en la tabla Facturas.

INSERT en la tabla Facturas
Comando para agregar un nuevo registro (factura) con todos sus valores correspondientes.

Tabla Auditoria
Se creó una tabla para registrar automáticamente mensajes informativos o de control sobre acciones que se realizan en la base de datos. Contiene:

ID_Auditoria: Identificador único, clave primaria con incremento automático.

Mensaje: Texto que describe la acción registrada.

FechaHora: Fecha y hora en que se registró el evento, con valor automático.

SELECT de la tabla Auditoria
Consulta que muestra todos los registros guardados en la tabla de auditoría.


## Paso 3: Ya que tenemos nuestra base de datos y tablas  creadas vamos a empezar. 
crearemos nuetros tigger
![Trigger Marketing](img5.png)


## Explicacion del codigo.
El código crea un trigger que se activa automáticamente después de insertar un registro en una tabla. Su función es ejecutar una acción definida, como registrar información en otra tabla. Utiliza una tabla virtual interna para acceder a los datos insertados y generar un mensaje o acción relacionada. Esto permite automatizar tareas sin intervención del usuario y mantener un registro consistente dentro de la base de datos.

## Este seria el resultado final.
![Trigger Marketing](img7.png)


## Características de un Trigger.
Se ejecuta automáticamente al ocurrir un evento.

No necesita ser llamado por el usuario.

Puede activarse antes o después de un INSERT, UPDATE o DELETE.

Ayuda a mantener el control y la integridad de los datos.

Está vinculado a una tabla específica.


## Desventajas de un Trigger.
Puede dificultar la depuración y el mantenimiento del sistema.

Aumenta la complejidad del diseño de la base de datos.

Si no se diseña bien, puede afectar el rendimiento.

Sus efectos no siempre son visibles para el usuario.


## Sustituto de los Triggers en otras bases de datos.
Aunque los triggers son útiles para automatizar tareas dentro de la base de datos, existen otras alternativas que pueden cumplir funciones similares, especialmente cuando se busca mayor control o claridad en la lógica del sistema.

Procedimientos almacenados: Son bloques de código SQL que se ejecutan manualmente o por programación. A diferencia de los triggers, no se activan automáticamente, pero permiten realizar tareas repetitivas con control total sobre cuándo y cómo se ejecutan.

ORMs (Mapeo Objeto-Relacional): Herramientas como Django (Python) o Hibernate (Java) permiten manejar la lógica de negocios desde el código de la aplicación. Esto facilita la visibilidad y el mantenimiento, ya que la lógica no queda oculta dentro de la base de datos.

Tareas programadas (jobs): Algunas bases de datos como SQL Server permiten programar tareas automáticas a través de herramientas como SQL Server Agent. También se pueden usar cron jobs en sistemas operativos para ejecutar scripts en horarios definidos, logrando efectos similares a los triggers pero con mayor planificación.

Estas alternativas son útiles cuando se busca una solución más visible, flexible o controlada desde el lado de la aplicación o del servidor.

¿Te gustaría que ahora te arme todo esto en formato README.md para que lo pegues directo en Visual Studio Code?












