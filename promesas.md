---
title: Qué es una promesa en JavaScript
nav_order: 8
---
## Qué es una promesa en JavaScript

<p><img width="597" height="288" alt="promesas_2" src="https://github.com/user-attachments/assets/33afcdea-ebf2-4d94-aba5-2c9b13b100cb" /></p>

Una promesa es un objeto que representa un valor que puede que esté disponible «ahora», en un «futuro» o que «nunca» lo esté. Como no se sabe cuándo va a estar disponible, todas las operaciones dependientes de ese valor, tendrán que posponerse en el tiempo. A esto se denomina *programación asíncrona*.

El uso de promesas facilita, en buena medida, el control de flujos de datos asíncronos en una aplicación.

Una de las formas más comunes de usar promesas es al comunicarnos con API externas y elegir qué elementos de tu página o aplicación se cargarán de inmediato y cuáles tardarán un poco más.

La convención más común es usar `resolve` y `reject`. Esto significa que se espera que una promesa funcione correctamente o que presente algún tipo de error o problema. Al crear una promesa, le indicamos al programa que recibirá una respuesta: una respuesta exitosa (si se comunica con una API, recibirá los datos y podrá gestionarlos); o, si hay un error, le devolveremos un error y le indicaremos cómo solucionarlo. En otras palabras, las promesas esperan éxitos y fracasos en los posibles resultados.

JavaScript se basa en la comunicación con servicios externos, ya sean bases de datos, API de backend o cualquier otro componente externo a la aplicación. Todos los frameworks, como React, Angular y View, obtienen sus datos comunicándose con servicios externos. Por lo tanto, el uso de herramientas como las promesas es fundamental para garantizar que este proceso se desarrolle de la manera más fluida posible.

Es crucial comprender cómo funciona una promesa y qué componentes necesita para su correcto funcionamiento.

La promesa en sí misma no aporta mucho; no se muestra directamente en pantalla, sino que se recibe como resultado un objeto de promesa. Luego, hay que procesarla. Debemos especificar qué hacer con una respuesta exitosa, pero también qué hacer en caso de fallo. 

La sintaxis básica podría ser la siguiente: 

```javascript
miPromesa
  .then((mensaje) => {
    console.log(mensaje); // Imprime el éxito
  })
  .catch((error) => {
    console.error(error); // Imprime el error
  });

```

**Métodos de las promesas en JavaScript**

Aquí están algunos de los métodos más comunes que puedes utilizar:

**`.then()`** : Este método se utiliza para manejar el resultado exitoso de una promesa. Recibe una función que se ejecutará cuando la promesa se resuelva con éxito y puede recibir el resultado como argumento.
**`.catch()`** : Se utiliza para manejar errores que puedan ocurrir durante la ejecución de la promesa. Puedes encadenar .catch() después de .then() para manejar errores específicos.

Veamos un ejemplo donde se ejecutan los dos anteriores. Observemos que la sintaxis utiliza **`arrow function`**: 

```javascript
function obtenerDatos() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const exito = true;
      if (exito) {
        resolve("Datos obtenidos con éxito");
      } else {
        reject("Error al obtener los datos");
      }
    }, 1000);
  });
}

obtenerDatos()
  .then(resultado => {
    console.log(resultado);
  })
  .catch(error => {
    console.error(error);
  });

```

**`.finally()`** : Este método se utiliza para ejecutar una función después de que la promesa se resuelva o se rechace, independientemente del resultado. Es útil para realizar tareas de limpieza o acciones que deben ocurrir sin importar el resultado de la promesa. El método .finally() toma una función de callback que se ejecuta de forma automática una vez que la promesa se establece. A diferencia de `.then()` o `.catch()`, el callback no recibe ningún argumento.

```javascript
mostrarIndicadorDeCarga();

fetch('/api/datos')
  .then(respuesta => respuesta.json())
  .then(datos => {
    console.log("Datos obtenidos con éxito:", datos);
  })
  .catch(error => {
    console.error("Ocurrió un error:", error);
  })
  .finally(() => {
    // Este código se ejecuta siempre, sin importar el éxito o fallo anterior
    ocultarIndicadorDeCarga();
    console.log("Operación de fetch finalizada.");
  });

```

**`Promise.all(iterable)`** : Este método permite manejar múltiples promesas al mismo tiempo y resuelve una promesa una vez que todas las promesas del iterable se hayan resuelto o alguna de ellas se haya rechazado.

```javascript
const greeting = new Promise((resolve, reject) =>{
  resolve('Hi there');
  reject('Oops, bad greeting');
});

const updateAccount = new Promise((resolve, reject) => {
  resolve('Updating last login...');
  reject('Error updating account with login.');
});

const loginActivities = Promise.all([greeting, updateAccount]);

loginActivities.then(res => {
  res.forEach(activity => {
    console.log(activity);
  })
})

```

**`Promise.race(iterable)`** : Este método resuelve una promesa tan pronto como una de las promesas en el iterable se resuelva o se rechace. Es útil cuando deseas obtener el resultado más rápido de múltiples promesas.

Una promesa puede estar en los siguientes tres estados:

- Pendiente (pending). Es el estado inicial al crear una promesa.
- Resuelta con éxito (fulfilled). Estará resuelta en el momento que llamemos a resolve y, a continuación, se ejecutará la función que pasamos al método .then. Debemos de tener en cuenta que, una vez resuelta, no podremos modificar el valor de la promesa, aunque sí podríamos correr la misma instrucción para obtener un valor distinto y hacerlo las veces que deseemos.
- Rechazada (rejected). También puede ocurrir que se complete pero sea rechazada por un error, pasando a continuación a ejecutar la función que pasamos a .catch.

Veamos el siguiente ejemplo de llamada a una API: 

```javascript

// Llamada a una API pública
fetch('https://typicode.com')
  .then(response => {
    if (!response.ok) {
      throw new Error('Error en la red');
    }
    return response.json(); // Convierte la respuesta a JSON
  })
  .then(data => {
    console.log("Título de la tarea:", data.title);
  })
  .catch(error => {
    console.error("Error al obtener los datos:", error);
  });

```
