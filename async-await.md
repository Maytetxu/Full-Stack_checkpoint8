---
title: Async y await
nav_order: 9
---
## Async y await

<p><img width="1269" height="373" alt="async_await" src="https://github.com/user-attachments/assets/8de9569c-bf08-4ca2-a4df-dbf69a3af4bd" /></p>

En el apartado anterior, analizamos las promesas en JavaScript. En el JavaScript moderno, es muy común utilizar **async** / **await**, que es una sintaxis más limpia (azúcar sintáctico) construida sobre las promesas. Nos permite escribir código asíncrono que parece síncrono.

Para entender la diferncia entre código asíncrono y síncrono pensemos en una llamada telefónica, como ejemplo de comunicación síncrona: cuando hablamos por teléfono, la información entra y sale en secuencia, una tras otra; hacemos una pregunta, inmediatamente recibimos la respuesta. Por otra parte, una conversación online a través de algún messenger, como WhatsApp o Telegram, es un ejemplo de comunicación asíncrona: enviamos un mensaje y no nos quedamos mirando la pantalla, esperando, hasta que la otra persona responda.

**¿Cómo funcionan?**

**`async`**: Se coloca antes de la declaración de una función para indicar que siempre devolverá una Promesa. Si la función retorna un valor simple, JavaScript lo envuelve automáticamente en una promesa resuelta.

**`await`**: Se utiliza solo dentro de una función declarada como async. Le indica a JavaScript que pause la ejecución de la función y espere a que la promesa se resuelva (o rechace) antes de pasar a la siguiente línea. Si no utilizamos await en una función asincrónica, seguramente el código se ejecutará en desorden, pues el programa continuaría leyendo mientras espera al resultado de una función no inmediata. 

Veamos el siguiente ejemplo de promesa con async/await: 

```javascript
let response = await fetch(`https://api.com/api/user/${userId}`);
let userData = await response.json();

Solo puede usar await en funciones declaradas con la palabra-clave async, así que agréguela:

async function getUser(userId) {
 let response = await fetch(`https://api.com/api/user/${userId}`);
 let userData = await response.json();
 return userData.name; // no es necesario await en el return
}

```
Una función declarada como async significa que el valor de retorno de la función será, "por dentro de javascript", una Promesa. Si la promesa se resuelve normalmente, el objeto-promesa retornará el valor. Si arroja una excepción, podemos usar try/catch como estamos acostumbrados en los programas síncronos.

Para ejecutar la función getUser(), ya que retorna una Promesa, puedes usar await:

```javascript
exibeDatosUser(await getUser(1))
```

Recordar que await solo funciona si está dentro de otra función async. Si todavía no estás familiarizado, puedes usar `.then()` normalmente:

```javascript
getUser(1).then(exibeDadosUser).catch(reject)

```
**Buenas prácticas**

Aunque `async/await` surgió como una opción de "lectura más fácil" que `.then()`, es importante tener en cuenta que estos métodos no son lógicamente equivalentes: mientras que `async/await` realiza el procesamiento secuencialmente, las promesas con .then() se procesan en paralelo , lo que hace que este método sea más rápido. async/await simplifica la escritura y la interpretación del código, pero no es tan flexible y solo funciona con una Promesa a la vez.

Si necesitamos manejar varias *promesas*, pero no queremos hacerlo en paralelo, por ejemplo, si necesitamos acceder a una base de datos con miles de registros. En este caso, no queremos que todas las solicitudes se realicen en paralelo, ya que el exceso de solicitudes simultáneas puede causar problemas de rendimiento e incluso la caída del servicio.
