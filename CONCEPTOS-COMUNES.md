# Conceptos compartidos y respuestas para la defensa

Estos conceptos son comunes a los nueve. El detalle de cada función corresponde a la guía individual; nadie necesita memorizar todo el sistema.

## ¿En qué está programado y qué hace cada parte?

Frontend y backend están en JavaScript. React construye pantallas y actualiza el estado visible; React Router elige qué pantalla mostrar. Express recibe las solicitudes HTTP. Los controladores aplican las reglas. Sequelize representa las tablas como modelos y genera consultas SQL; mysql2 conecta con MySQL 8.4. Zod valida los datos que llegan a la API.

MySQL es el motor de base de datos, no un lenguaje alternativo del programa. SQL es el lenguaje con el que se consulta la base; Sequelize genera gran parte de esas consultas.

## ¿Cómo llega una acción de pantalla a la base?

```text
Botón/formulario React
  -> api() en client/src/lib.jsx
  -> ruta Express /api/v1/...
  -> sesión, permiso y esquema de validación
  -> controlador de la funcionalidad
  -> transacción y modelo Sequelize
  -> MySQL
  -> respuesta pública y actualización de React
```

No alcanza con cambiar un estado en React: eso puede desaparecer al recargar. Guardar en MySQL permite recuperar los datos en una nueva consulta.

## ¿Cuál es la diferencia entre una pantalla y una API?

`/rutinas` es una dirección del navegador que muestra la biblioteca. `/api/v1/routines` es una ruta HTTP que devuelve o recibe JSON. Una misma pantalla puede llamar a varias rutas. En una modificación, no hay que confundir GET para consultar, POST para crear/ejecutar una acción, PUT/PATCH para actualizar y DELETE para eliminar.

## ¿Qué diferencia hay entre ruta, controlador y modelo?

La ruta decide a qué operación se llega y valida el contrato de entrada. El controlador decide si la operación corresponde, comprueba las reglas y coordina el guardado. El modelo representa la tabla. Separarlos permite cambiar la pantalla sin escribir SQL dentro de React.

## ¿Qué es autenticación y qué es autorización?

Autenticación identifica quién tiene una sesión válida. Autorización comprueba si esa persona puede realizar esa operación. Aunque una persona haya iniciado sesión, no debe poder leer una rutina ajena. La API comprueba propietario/permisos; esconder un botón en React no alcanza.

## ¿Cómo funciona una sesión?

El servidor crea un token aleatorio y guarda su hash, usuario y vencimiento. El navegador recibe una cookie HttpOnly: JavaScript no puede leerla directamente. La API comprueba esa cookie en cada solicitud privada. Cerrar sesión revoca la sesión; no es solo volver a la pantalla de login. La preentrega y el final usan cookies distintas para no interferir al ejecutarlos juntos.

## ¿Se guarda la contraseña tal como se escribe?

No. Se guarda un hash con scrypt y sal. En login se comprueba la contraseña contra ese hash; no se descifra. El teléfono sí necesita poder recuperarse para mostrarlo: se cifra con AES-256-GCM y una clave privada del servidor. Hash de contraseña y cifrado reversible son conceptos distintos.

## ¿Por qué validar tanto en React como en Express?

La validación en pantalla ayuda a corregir un formulario. La validación del servidor es obligatoria porque una petición puede enviarse sin usar la pantalla. Se comprueban tipos, rangos, fechas, permisos y reglas como tener un único objetivo activo. Un error debe explicarse sin mostrar datos internos o claves.

## ¿Qué es una transacción?

Agrupa cambios que deben quedar juntos. Si al guardar una rutina falla un ejercicio, la operación no debe dejar una rutina incompleta. El guardado se confirma si toda la operación termina bien; si falla, se revierte. En este proyecto también se verifican firmas y se registra bitácora dentro del flujo.

## ¿Qué son bitácora y DVH/DVV?

La bitácora registra eventos. DVH firma filas y DVV verifica el conjunto de una tabla mediante HMAC. Permiten detectar alteraciones fuera de las operaciones autorizadas. No prueban que nunca pueda haber ataques. Si hay una diferencia, no se deben recalcular firmas a mano para ocultarla.

## ¿Qué significa borrar una cuenta y qué es una baja lógica?

La cuenta propia exige contraseña y confirmación; se eliminan sus datos dependientes y se revocan accesos. Algunas entidades, como una rutina, se dan de baja cambiando su estado para conservar el historial de entrenamientos. Cada módulo debe explicar su comportamiento concreto. Cancelar un diálogo no debe enviar la operación destructiva.

## ¿La IA es real? ¿Dónde está la clave?

Con `AI_MOCK=false` y una clave válida, Node llama por HTTPS a Cohere. No corre Llama ni otro modelo local. La clave está en el entorno privado del backend y no se entrega a React ni se publica. La preentrega solo tiene chat con historial; el sistema final además genera/adapta rutinas y dietas. El usuario debe otorgar consentimiento y puede revocarlo.

`AI_MOCK=true` usa respuestas de diagnóstico: no demuestra conexión real. Cohere puede fallar o agotar cuota. El programa debe informar el error y no guardar una respuesta o plan parcial. La orientación de IA no reemplaza a un profesional.

## ¿Cómo explicamos el “50%”?

La preentrega selecciona 20 de 39 casos nominales: aproximadamente la mitad. No mide la mitad de las líneas ni del esfuerzo. CU014 tiene su navegación recortada a rutinas manuales. Nutrición, administración y generación/adaptación IA de planes están fuera de esa versión. Una tabla futura del DER o un método UML declarado no cuentan por sí solos como una función terminada.

## ¿Qué pasa si el profesor pregunta algo que no comprobamos?

Describir lo que el código hace y lo que se verificó. Por ejemplo, recuperación por archivo local no equivale a correo enviado; compilación exitosa no equivale a revisión visual; una comprobación de Cohere no garantiza disponibilidad futura. No inventar autorías, resultados o respuestas exitosas.

## Ensayo rápido entre los nueve

Cada integrante ubica una función de su guía, describe entrada/regla/salida, la demuestra en pantalla, provoca un error controlado y recarga para comprobar persistencia. El compañero que recibe sus datos explica cómo los utiliza. Registrar los aportes efectivos en el reparto correspondiente.
