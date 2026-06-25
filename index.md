---
description: Bucles, variables, arrow function, POO y API's query
---

# JavaScript

## Tipos de bucles en JavaScript
<p><img width="633" height="484" alt="loops_2" src="https://github.com/user-attachments/assets/52938b0d-4684-4276-a1d4-12450b75f28f" /></p>

¿Alguien recuerda el famoso castigo de las novelas de Charles Dickens donde los estudiantes tenían que escribir líneas repetidamente en una pizarra? Imaginemos que la orden "escribe esta frase 100 veces" se pudiese hacer automáticamente. Eso es exactamente lo que hacen los bucles para código.

Los bucles son como tener un asistente incansable que puede repetir tareas sin error. Ya sea que necesites revisar cada artículo en un carrito de compras o mostrar todas las fotos de un álbum, los bucles manejan la repetición de manera eficiente.

JavaScript ofrece varios tipos de bucles para elegir. Analicemos cada uno y entendamos cuándo usarlos.

Hay diferentes tipos de bucles, pero esencialmente, todos hacen lo mismo: repiten una acción varias veces. (¡Es posible que ese número sea cero!).

Los diversos mecanismos de bucle ofrecen diferentes formas de determinar los puntos de inicio y terminación del bucle. Hay varias situaciones que son mejor atendidas por un tipo de bucle que por otros.

Las declaraciones para bucles proporcionadas en JavaScript son:

1. Bucle for
2. Bucle for...in
3. Declaración for...of
4. Bucle while
5. Bucle do...while
6. Método forEach
7. Declaración break
8. Declaración continue
9. Switch-case

#### **1. Bucle For**

El bucle `for` es como poner un temporizador: sabes exactamente cuántas veces quieres que algo suceda. Es súper organizado y predecible, lo que lo hace perfecto cuando trabajas con arrays o necesitas contar cosas. 

```javascript
for (var i = 0; i < 5; i++) {
  console.log("El valor de i es: " + i);
}
```

En este ejemplo, la variable `i` se utiliza para llevar un registro del número de veces que se ha ejecutado el bloque de código dentro del `for`. La sentencia `for` inicializa `i` con un valor de 0. Mientras que `i` sea menor que 5, se ejecutará el bloque de código, mostrando en la consola el valor actual de `i` con el mensaje "El valor de i es: " y aumentando el valor de `i` en cada iteración.

#### **2. Bucle For-in**



La sentencia `for-in` se utiliza para recorrer las propiedades de un objeto.

```javascript
var persona = {
  nombre: "Ana",
  edad: 28,
  pais: "España"
};

for (var propiedad in persona) {
  console.log("La propiedad " + propiedad + " tiene el valor " + persona[propiedad]);
}
```

En este ejemplo, la variable `propiedad` se utiliza para llevar un registro del nombre de la propiedad que se está recorriendo en cada iteración. La sentencia `for-in` recorre las propiedades del objeto `persona` y, en cada iteración, muestra en la consola el nombre de la propiedad junto con su valor correspondiente, utilizando la sintaxis `persona[propiedad]`.



#### **3. Declaración for-of** <a href="#declaracion_for...of" id="declaracion_for...of"></a>

La declaración `for...of` crea un bucle que se repite sobre objetos iterables (incluidos Array, Map, Set, objetos arguments y así sucesivamente), invocando un bucle de iteración personalizado con declaraciones que se ejecutarán para el valor de cada distinta propiedad.

```javascript
for (variable of objeto)
  expresión
```

El siguiente ejemplo muestra la diferencia entre un bucle `for...of` y un bucle `for...in`. Mientras que `for...in` itera sobre los nombres de propiedad, `for...of` itera sobre los valores de propiedad:

```javascript
const arr = [3, 5, 7];
arr.foo = "hola";

for (let i in arr) {
  console.log(i); // logs "0", "1", "2", "foo"
}

for (let i of arr) {
  console.log(i); // logs 3, 5, 7
}
```

#### **4. Bucle While**

El bucle `while` es como decir "sigue haciendo esto hasta que..." - puede que no sepas exactamente cuántas veces se ejecutará, pero sabes cuándo detenerlo. En otras palabras, repite un bloque de código mientras se cumpla una condición determinada. Es perfecto para cosas como pedir entrada al usuario hasta que proporcione lo necesario, o buscar datos hasta encontrar lo que buscas.

```javascript
var contador = 0;

while (contador < 5) {
  console.log("El contador es: " + contador);
  contador++;
}
```

En este ejemplo, la variable `contador` se utiliza para llevar un registro del número de veces que se ha ejecutado el bloque de código dentro del `while`. Mientras que el valor de `contador` sea menor que 5, el bloque de código se seguirá ejecutando, mostrando en la consola el valor actual de `contador` con el mensaje "El contador es: " y aumentando el valor de `contador` en cada iteración.

**Características del bucle While:**

* **Continúa** ejecutando mientras la condición sea verdadera.
* **Requiere** manejar manualmente las variables contador.
* **Verifica** la condición antes de cada iteración.
* **Riesgo** de bucles infinitos si la condición nunca se vuelve falsa.

#### **5. Bucle do-while**

La sentencia `do-while` se utiliza para repetir un bloque de código al menos una vez y luego mientras se cumpla una condición determinada.

```javascript
var numero = 0;

do {
  console.log("El número es: " + numero);
  numero++;
} while (numero < 5);
```

En este ejemplo, la variable `numero` se utiliza para llevar un registro del número de veces que se ha ejecutado el bloque de código dentro del `do`. El bloque de código se ejecutará al menos una vez, mostrando en la consola el valor actual de `numero` con el mensaje "El número es: " y aumentando el valor de `numero` en cada iteración. La sentencia `while` evalúa si el valor de `numero` es menor que 5 y, mientras que esto sea cierto, se seguirá repitiendo el bloque de código dentro del `do`.

#### **6. Método forEach**

<p><img width="1212" height="532" alt="forEach" src="https://github.com/user-attachments/assets/eb39406e-4300-4a6f-98eb-5b792487634b" /></p>

Considerada una forma de bucle más moderna para trabajar con colecciones:

* **Ejecuta** una función para cada elemento del array.
* **Proporciona** tanto el valor del elemento como el índice como parámetros.
* **No puede** ser detenido anticipadamente (a diferencia de bucles tradicionales).
* **Devuelve** undefined (no crea un nuevo array).

La sintaxis básica de un bucle `forEach` en JavaScript es la siguiente:

```javascript
colección.forEach((elemento) => {
// Código a ejecutar para cada elemento de la colección
});
```

Vamos a verlo con un ejemplo simple donde se utilizamos un bucle `forEach` para iterar sobre un array de números:

```javascript
let numeros = [1, 2, 3, 4, 5];

numeros.forEach(function(numero) {
    console.log(numero);
});
```

También es posible utilizar _Arrow Functions_ (explicaremos esta función más adelante con detalle) en lugar de funciones anónimas en la sintaxis de `forEach` _(de hecho es muy habitual)_.

```javascript
array.forEach((element) => {
  // Código a ejecutar para cada elemento
});
```

El ejemplo anterior utilizando arrow functions quedaría así:

```javascript
const numeros = [1, 2, 3, 4, 5];

numeros.forEach((numero) => {
  console.log(numero);
});
```

Es importante mencionar que el método `forEach` no retorna un array nuevo. Este tiene como función principal iterar y ejecutar una función sobre cada elemento del array en Javascript.

#### **7. Break**

La instrucción _break_ en JavaScript **representa un alto completo en el bucle.** Es decir, cuando el programa se encuentra con esta palabra, interpreta que debe detener el bucle actual. Esta palabra se usa normalmente junto al condicional _if._ Entonces, podemos definir que si una variable llega a ser determinado valor, el bucle se detiene. Después de leer **break,** el programa pasa a leer la siguiente línea de código de nuestro archivo.

```javascript
function comprobarBreak(x) {
var i = 0;
while (i < 6) {
if (i == 3) break;
i++;
}
return i * x;
}
```

#### **8. Continue**

La instrucción _continue_ en JavaScript es menos severa que la instrucción _break._ Esta nos permite, en vez de terminar el bucle, **saltar una parte de su función.** De este modo, esa sección no será modificada por el bucle, pero este podrá seguir con la siguiente iteración. Entonces, cuando el programa se topa con un _continue,_ **este interpreta que debe ignorar lo que hay desde esta palabra hasta el final del bucle actual.** Después de ignorarlo, sigue con la siguiente iteración. Es decir, el bucle no finaliza, pero sí se modifica su función, pues ya no ejecutará la parte final de su comportamiento inicial.

```javascript
i = 0;
n = 0;
while (i < 5) {
  i++;
  if (i == 3) {
    continue;
  }
  n += i;
}
```

#### **9. Switch**

En _JavaScript_, la sentencia `switch` es una estructura de control que nos permite ejecutar diferentes bloques de código dependiendo del valor de una **expresión**. Esta estructura es útil cuando queremos realizar diferentes acciones basadas en una única variable.

**Sintaxis**

La sentencia `switch` evalúa una **expresión**, comparando el valor con los diferentes **casos** que le hemos definido. Si hay coincidencia ejecuta el bloque de código asociado. Para ello, se utiliza la sentencia `break` para separar cada caso y evitar que se sigan evaluando el resto de casos.

```javascript
switch (expresión) {
  case valor1:
    // código a ejecutar si la expresión coincide con valor1
    break

  case valor2:
    // código a ejecutar si la expresión coincide con valor2
    break
  default:
    // código a ejecutar si la expresión no coincide con ningún valor
    break
}
```

Switch-case puede considerarse tanto un condicional, como una estructura de control de flujo, es por ello que lo mencionamos en este apartado. 

* **Control de flujo:** Permite al programa tomar decisiones y cambiar su camino de ejecución según el estado de los datos, actuando como una alternativa más limpia a múltiples bloques `if...else if`.
* **Condicional:** Funciona comparando si el valor de la expresión coincide estrictamente (===) con el valor de cada `case`. 

Podremos verlo con claridad en el siguiente ejemplo:

```javascript
const mascota = "perro";
 
switch (mascota) {
  case "lagarto":
    console.log("Tengo un lagarto");
    break;
  case "perro":
    console.log("Tengo un perro");
    break;
  case "gato":
    console.log("Tengo un gato");
    break;
  case "serpiente":
    console.log("Tengo una serpiente");
    break;
  case "loro":
    console.log("Tengo un loro");
    break;
  default:
    console.log("No tengo mascota");
    break;
}
```

La siguiente tabla muestra un resumen de los bucles e instrucciones de control de flujo:


| Tipo de bucle o instrucción       | ¿Qué hace?                                                                                                                             |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Declaración `for`**             | Repite un bloque de código un número determinado de veces mediante una inicialización, una condición y una expresión de actualización. |
| **Declaración `for...in` \***     | Recorre las propiedades enumerables de un objeto. No se recomienda para recorrer arrays.                                               |
| **Declaración `for...of` \*\***   | Recorre los valores de objetos iterables, como arrays, strings, `Map` y `Set`.                                                         |
| **Declaración `while`**           | Ejecuta un bloque de código mientras una condición sea verdadera.                                                                      |
| **Declaración `do...while`**      | Ejecuta un bloque de código al menos una vez y continúa repitiéndolo mientras la condición sea verdadera.                              |
| **Método `forEach()`**            | Ejecuta una función una vez por cada elemento de un array. No permite utilizar `break` ni `continue`.                                  |
| **Declaración `break` \*\*\***    | Interrumpe inmediatamente la ejecución de un bucle o una instrucción `switch`.                                                         |
| **Declaración `continue` \*\*\*** | Omite la iteración actual de un bucle y continúa con la siguiente.                                                                     |
| **Declaración `labeled`**\*\*\*\* | Asigna una etiqueta a un bloque o bucle para poder controlarlo mediante `break` o `continue`.                                          |
| **Declaración `switch`**          | Ejecuta diferentes bloques de código según el valor de una expresión.                                                                  |

#### Notas

* **\*for...in** está pensado para recorrer propiedades de objetos, no elementos de arrays.
* **\*\*for...of** es la forma moderna y recomendada para recorrer arrays y otros objetos iterables.
* **\*\*\*break** y **continue** no son bucles propiamente dichos, sino instrucciones de control del flujo.
* **\*\*\*\*labeled** es una característica avanzada y de uso poco frecuente en código moderno.

### Buenas prácticas



* Utilizar el bucle más apropiado para la tarea. Los bucles `for` son útiles para iterar sobre un rango de números, mientras que los bucles `while` son útiles para iterar mientras se cumpla una condición.
* Ser consciente del número de iteraciones que se realizarán. En algunos casos, puede ser más eficiente utilizar un bucle `for` en lugar de un bucle `while`, ya que se conoce de antemano el número de iteraciones.
* Evitar bucles infinitos. Asegurarse de que la condición de finalización del bucle sea alcanzable. Si no se cumple la condición de finalización, el bucle se ejecutará indefinidamente y puede causar problemas de rendimiento o errores en la aplicación.
* Utilizar nombres descriptivos y legibles para las variables de los bucles. Esto hace que el código sea más fácil de entender y depurar.
* No modificar la variable de control dentro del bucle. Si es necesario modificar la variable de control, asegurarse de que la condición de finalización del bucle siga siendo alcanzable.
* Evitar las operaciones costosas dentro del bucle. Si es posible, realizar las operaciones costosas fuera del bucle o en una iteración separada.

Siguiendo estas buenas prácticas en los bucles en JavaScript, podemos escribir código más legible, eficiente y menos propenso a errores sutiles.

## `const`, `let` y `var` Diferencias y usos

<p><img width="597" height="335" alt="var_const_let" src="https://github.com/user-attachments/assets/26830546-c978-4435-8f9a-a423e93fadfb" /></p>

Una de las características que llegaron con ES6 es la adición de `let` y `const`, que se pueden utilizar para la declaración de variables. La pregunta es, ¿qué las hace diferentes del viejo `var` que hemos venido utilizando?.

En este apartado explicaré  `var`, `let` y `const`  con respecto a su ámbito (alcance), uso y hoisting.

Antes de la llegada de ES6, las declaraciones `var` eran las que mandaban. Sin embargo, hay problemas asociados a las variables declaradas con `var`. Por eso fue necesario que surgieran nuevas formas de declarar variables. En primer lugar, vamos a entender más sobre `var` antes de discutir esos problemas.

**Hoisting**

Antes de explicar estas tres formas de declarar una variable, es necesario comprender lo que significa "hoisting" (elevar, en inglés).

Hoisting es cuando las funciones y las variables se almacenan en memoria para un contexto de ejecución antes de ejecutar nuestro código. 

Hoisting en JavaScript, nos permite acceder a funciones y variables antes de que hayan sido creadas.

El hoisting funciona de forma diferente si la declaración de la variable se realiza mediante `let` o `const`.

En el caso de `var` el valor se inicializa a indefinido (undefined) durante la fase de creación. Sin embargo, en el caso de `let` y `const` el valor sólo se inicializa durante la fase de ejecución.

<p align="center">
  <img width="876" height="652" alt="var_const_let2" src="https://github.com/user-attachments/assets/0475dbc4-8d8a-47e3-b96b-d61f420f09c4" /><br>
  <sub>Declaración de variables, explicado con manzanas</sub>
</p>


#### **`var`** 

La declaración de variables usando `var` fue la forma original de declarar variables en JavaScript, lo que lo hace compatible con todas las versiones del lenguaje. En la actualidad, ésto tiene algunas limitaciones importantes, especialmente en términos de ámbito.

**Ámbito de `var`**

El ámbito, significa esencialmente dónde están disponibles estas variables para su uso. Las declaraciones `var` tienen un ámbito global o un ámbito de función/local.

El ámbito es global cuando una variable `var` se declara fuera de una función. Esto significa que cualquier variable que se declare con `var` fuera de una función está disponible para su uso en toda la pantalla.

`var` tiene un ámbito local cuando se declara dentro de una función. Esto significa que está disponible y solo se puede acceder a ella dentro de esa función.

Para entenderlo mejor, mira el siguiente ejemplo.

```javascript
    var saludar = "hey, hola";
    
    function nuevaFuncion() {
        var hola = "hola";
    }
    console.log(hola); // error: hola is not defined
```

Esto ocurre, porque, en este ejemplo, `var` tiene un ámbito local y no está disponible fuera de la función. 

En términos de declaraciones, `var` se puede volver a declarar, pero `let` y `const` no. Entonces, cuando usa `var`, puede hacer algo como esto:

```
var greeting = "Hello";
var greeting = "Hello, hello, everyone";
```

#### **`let`** <a href="#let" id="let"></a>

`let` es ahora preferible para la declaración de variables. No es una sorpresa, ya que es una mejora de las declaraciones con `var`. También resuelve el problema con `var` que acabamos de describir. 

**Ámbito de** **`let`**

Un bloque es un trozo de código delimitado por {}. Un bloque vive entre llaves. Todo lo que está dentro de llaves es un bloque.

Así que una variable declarada en un bloque con `let`  solo está disponible para su uso dentro de ese bloque, a diferencia de lo que ocurre con `var`. A esto se le denomina *block scope*. Permíteme explicar esto con un ejemplo:

```javascript
   let saludar = "dice Hola";
   let tiempos = 4;

   if (tiempos > 3) {
        let hola = "dice Hola tambien";
        console.log(hola);// "dice Hola tambien"
    }
   console.log(hola) // hola is not defined

```

En otras palabras, `let` _puede modificarse pero no volver a declararse_.

Al igual que `var`,  una variable declarada con `let` puede ser actualizada dentro de su ámbito. A diferencia de `var`, una variable `let` no puede ser re-declarada dentro de su ámbito. Así que mientras esto funciona:


```javascript
    let saludar = "dice Hola";
    saludar = "dice Hola tambien";
```


#### **`Const`**

Las variables declaradas con `const` mantienen valores constantes. Las declaraciones `const` mantienen similitudes con las declaraciones `let`.

Las declaraciones `const` tienen un ámbito de bloque. Al igual que las declaraciones `let`, ya que solo se puede acceder a las declaraciones `const` dentro del bloque en el que fueron declaradas. 

Esto significa que `const` _no puede modificarse ni volver a declararse_. Tampoco se puede actualizar. Así que si declaramos una variable con `const`, no podemos hacer esto:

```javascript
const saludar = "dice Hola";
saludar = "dice Hola tambien";// error: Assignment to constant variable. 
```

Ni tampoco esto: 

```javascript
const saludar = "dice Hola";
const saludar = "dice Hola tambien";// error: Identifier 'saludar' has already been declared
```

**Buenas prácticas**

Las funciones se almacenan con una referencia a las funciones completas, las variables declaradas con `var` con el valor de `undefined`, y las variables declaradas con `let` y `const` se almacenan sin inicializar.

Las mejores prácticas sugieren declarar las variables al principio del bloque de código. También es preferible utilizar `let` y `const` para la declaración de variables. Esto mejora la legibilidad del código.

Aunque el uso de la declaración de variables mediante `var` se ha convertido en algo obsoleto, es importante conocer este concepto, ya que es posible que lo encontremos en algunas de las bases de código existentes o incluso en una entrevista donde debamos refactorizar dicho código con las últimas características de JavaScript.

## Arrow function

<p><figure><img width="738" height="414" alt="arrow_function" src="https://github.com/user-attachments/assets/3b6dd48a-7880-483e-8755-9c253f52dca0" /><figcaption></figcaption></figure></p>

Las **funciones flecha** o **arrow functions** son uno de los aspectos más importantes que debemos aprender en JavaScript moderno. Su uso está muy extendido, y si nunca las has visto o trabajado con ellas, pueden parecer un poco intimidantes.
Su aspecto es completamente diferente al de cualquier otro tipo de declaración de función que hayamos visto si solo has usado JavaScript puro, en versiones antiguas.

Utiliza la sintáxis **=>** para definir las funciones de una manera más compacta y fácil de interpretar.

Es importante subrayar que las **arrow function son anónimas**, lo que significa que no tienen nombre.

Este anonimato crea algunos problemas:

*a) Más difíciles de depurar*. Cuando obtengas un error, no serás capaz de rastrear el nombre de la función o el número de línea exacto donde ocurrió.

*b) Sin autorreferencia*. Si tu función necesita tener autorreferencia en algún punto (por ejemplo, recursión, controlador de evento que necesita desvincularse), no funcionará.

La sintaxis de `arrow function`, como podemos observar en la imagen, integra la función (paréntesis), flecha (arrow function) y corchetes (cuerpo de la función):

```javascript
const nombreFuncion = (parametros) => {
 // cuerpo de la función
 return valor;
};
```

Tipos de **arrow function** en diferentes ámbitos:

1. **Función sin parámetros**

```javascript
const sayHello = () => {
 return 'Hello!';
};
console.log(sayHello()); // 'Hello!'
```

2. **Función con un solo parámetro**

Si hay un solo parámetro, se pueden omitir los paréntesis:

```javascript
const square = x => {
 return x * x;
};
console.log(square(4)); // 16 
```

3. **Función con múltiples parámetros**

```javascript
const add = (a, b) => {
 return a + b;
};
console.log(add(3, 5)); // 8
```

4. **Función con cuerpo conciso**

Si el cuerpo de la función contiene una sola expresión, se pueden omitir las llaves y el return:

```javascript
const multiply = (a, b) => a * b;
console.log(multiply(2, 3)); // 6
```

**Características de las funciones de flecha:**

* _**Sintaxis más concisa**_: Las funciones de flecha permiten escribir funciones de forma más breve.
* _**No tienen su propio this**_: El valor de this dentro de una función de flecha es el mismo que el valor de this en el entorno donde se definió la función (contexto léxico).

**Diferencias con las funciones tradicionales**:

* _**Contexto this**_: En funciones tradicionales, el valor de this puede cambiar dependiendo de cómo se invoque la función. Como se ha indicado en líneas anteriores, en funciones de flecha, this está ligado al contexto en el que se definió la función.

```javascript
function TraditionalFunction() {
 this.value = 1;
 setTimeout(function() {
 this.value++;
 console.log(this.value); // undefined (o error en modo estricto)
 }, 1000);
}
function ArrowFunction() {
 this.value = 1;
 setTimeout(() => {
 this.value++;
 console.log(this.value); // 2
 }, 1000);
}
new TraditionalFunction();
new ArrowFunction();
```

* **No pueden ser usadas como constructores**: Las funciones de flecha no pueden ser usadas con new para crear instancias. Intentar hacerlo resultará en un error.
* **No tienen acceso a argumentos**: Las funciones de flecha no tienen su propio objeto-argumento. Para acceder a los argumentos, se debe usar el operador rest (...args).

Ejemplo:

```javascript
// Función tradicional
function Person() {
 this.age = 0;
 setInterval(function() {
 this.age++;
 console.log(this.age); // En una función tradicional, `this` no es lo que se espera
 }, 1000);
}
new Person(); // El valor de `this` no se refiere a la instancia de Person
// Función de flecha
function Person() {
 this.age = 0;
 setInterval(() => {
 this.age++; // En una función de flecha, `this` se refiere al contexto léxico
 console.log(this.age);
 }, 1000);
}
new Person(); // El valor de `this` es correcto y se refiere a la insta
```

## Deconstrucción de objetos y variables

<p><img width="686" height="386" alt="deconstrucción_variables2" src="https://github.com/user-attachments/assets/8cb9fdac-db18-461b-a85f-c1b3fb458f8f" /></p>

Una de las características introducidas en las recientes actualizaciones de JavaScript es la deconstrucción (o deconstruction) de objetos y variables. La deconstrucción permite extraer propiedades de objetos y arreglos de manera más concisa y legible. A continuación, exploraremos en detalle qué es la deconstrucción de objetos, cómo se usa y algunos casos prácticos.

**¿Qué es la deconstrucción de objetos?**
La deconstrucción de objetos es una sintaxis que permite desempacar valores de arreglos o propiedades de objetos en variables distintas. Esto se hace utilizando una sintaxis similar a la de creación de objetos y arreglos. Veamos un ejemplo básico:

```javascript
const persona = {
  nombre: 'Juan',
  edad: 30,
  ciudad: 'Mazatlán'
};

const { nombre, edad, ciudad } = persona;

console.log(nombre); // Juan
console.log(edad);   // 30
console.log(ciudad); // Mazatlán
```
En este ejemplo, el objeto persona tiene tres propiedades: nombre, edad y ciudad. Utilizando la sintaxis de deconstrucción, creamos tres variables (nombre, edad y ciudad) y les asignamos los valores correspondientes del objeto persona.

**La deconstrucción permite asignar valores por defecto**

Es posible asignar valores por defecto a las variables si la propiedad que se intenta deconstruir no existe en el objeto. Esto se hace utilizando el operador `=`.

```javascript
const persona = {
  nombre: 'Juan',
  edad: 30
};

const { nombre, edad, ciudad = 'Desconocida' } = persona;

console.log(ciudad); // Desconocida

```
En este ejemplo, la propiedad ciudad no existe en el objeto persona, por lo que la variable ciudad toma el valor por defecto 'Desconocida'.

**Renombrar variables**

La deconstrucción de objetos también nos permite renombrar las variables mientras se deconstruye un objeto utilizando la sintaxis propiedad: nuevoNombre.

```javascript
const persona = {
  nombre: 'Juan',
  edad: 30
};

const { nombre: nombreCompleto, edad: años } = persona;

console.log(nombreCompleto); // Juan
console.log(años);           // 30

```
En este ejemplo, la propiedad nombre se deconstruye en la variable nombreCompleto y edad en años.

**Deconstrucción en objetos anidados**

La deconstrucción también puede ser utilizada en objetos anidados, permitiendo extraer propiedades de objetos dentro de otros objetos.
```javascript
const persona = {
  nombre: 'Juan',
  direccion: {
    ciudad: 'Mazatlán',
    pais: 'México'
  }
};

const { nombre, direccion: { ciudad, pais } } = persona;

console.log(ciudad); // Mazatlán
console.log(pais);   // México

```
En este ejemplo, extraemos ciudad y pais del objeto direccion que está anidado dentro del objeto persona.

**Deconstrucción con parámetros de función**
La deconstrucción de objetos es especialmente útil cuando se trabaja con parámetros de funciones, permitiendo pasar objetos completos y deconstruir sus propiedades directamente al establecer la función y sus parámetros (*firma de la función*).

```javascript
function mostrarInformacion({ nombre, edad, ciudad }) {
  console.log(`Nombre: ${nombre}`);
  console.log(`Edad: ${edad}`);
  console.log(`Ciudad: ${ciudad}`);
}

const persona = {
  nombre: 'Juan',
  edad: 30,
  ciudad: 'Mazatlán'
};

mostrarInformacion(persona);
```
En este ejemplo, la función mostrarInformacion recibe un objeto y deconstruye sus propiedades directamente en los parámetros.

**Deconstrucción para el intercambio de variables**

Otros lenguajes de programación permiten intercambiar valores de una manera mucho más eficiente. Las versiones modernas de JavaScript permiten algo muy parecido. Solo hay que recordar poner los valores entre corchetes a ambos lados de la asignación, como veremos en el ejemplo siguiente. 
```javascript
let a = 1, b = 2;
[a, b] = [b, a];

console.log(a); // 2
console.log(b); // 1
```
Esto es muy útil en diversas situaciones. Una de las principales es al implementar algoritmos. Uno de los procesos más comunes al implementar algoritmos de fusión, ordenación rápida o cualquier otro algoritmo avanzado, es la capacidad de intercambiar valores de variables sin necesidad de construir variables. Esto es muy difícil de lograr. Afortunadamente, gracias a esta funcionalidad en las versiones modernas de JavaScript, podemos hacerlo de una manera mucho más eficiente que con una sola línea de código.

**Deconstrucción en la importación de módulos**

Otro uso práctico de la deconstrucción es en la importación de módulos. Cuando importamos varios elementos de un módulo, podemos deconstruirlos directamente en la declaración de importación.

```javascript
import { useState, useEffect } from 'react';

// Uso de useState y useEffect

```
En este ejemplo, deconstruimos useState y useEffect directamente desde el módulo 'react'.

**Deconstrucción en bucles**

La deconstrucción puede ser utilizada en ciclos para iterar sobre arreglos de objetos y extraer sus propiedades de manera concisa.

```javascript

const personas = [
  { nombre: 'Juan', edad: 30 },
  { nombre: 'Ana', edad: 25 },
  { nombre: 'Luis', edad: 28 }
];

for (const { nombre, edad } of personas) {
  console.log(`Nombre: ${nombre}, Edad: ${edad}`);
}

```
En este ejemplo, iteramos sobre un arreglo de objetos personas y deconstruimos nombre y edad directamente en el ciclo for...of.

**Deconstrucción y rest operator**

La deconstrucción se puede combinar con el operador rest (...) para capturar el resto de las propiedades de un objeto en una nueva variable. En este ejemplo, nombre y edad se extraen del objeto persona, y el resto de las propiedades (ciudad y profesion) se agrupan en el objeto resto:

```javascript
const persona = {
  nombre: 'Juan',
  edad: 30,
  ciudad: 'Mazatlán',
  profesion: 'Ingeniero'
};

const { nombre, edad, ...resto } = persona;

console.log(nombre); // Juan
console.log(edad);   // 30
console.log(resto);  // { ciudad: 'Mazatlán', profesion: 'Ingeniero' }
```

**Deconstrucción de Arrays**

La deconstrucción también funciona con arrays, como en este ejemplo:

```javascript
const [primero, segundo, ...resto] = [1, 2, 3, 4, 5];
console.log(primero); // 1
console.log(segundo); // 2 console.log(resto);   // [3, 4, 5]
```

**Ventajas de la deconstrucción de objetos:**

Como ya hemos visto, la deconstrucción tiene múltiples usos y ventajas, tales como: 

* Código más limpio y legible: La deconstrucción reduce la cantidad de líneas de código necesarias para extraer propiedades de un objeto.
* Asignación simultánea: Permite asignar múltiples variables en una sola línea, haciendo el código más compacto.
Valores por defecto: La deconstrucción permite asignar valores por defecto a variables si la propiedad no existe en el objeto.
* Renombrado de variables: Se pueden renombrar las variables al deconstruir, lo que es útil para evitar conflictos de nombres.

En resumen, la **deconstrucción de objetos en JavaScript** es una característica poderosa que mejora la legibilidad y eficiencia del código. Permite extraer propiedades de objetos de manera concisa, asignar valores por defecto, renombrar variables y trabajar con objetos anidados y parámetros de funciones. Su uso adecuado puede simplificar considerablemente la manipulación de datos, especialmente en aplicaciones complejas y al trabajar con APIs.


## Operador de extensión en JS

<p><img width="686" height="386" alt="spread" src="https://github.com/user-attachments/assets/f0fc5698-cd56-4b1f-937f-b756e5bff57f" /></p>

Producto también de las nuevas versiones de JavaScript, es el operador de extensión o spread operator, del que hablaremos en este apartado. 

El spread operator que incorpora ECMAScript 6 en JavaScript es un operador que simplifica la recogida de valores en una estructura de datos. Su representa con tres puntos: ...

La definición que nos da Mozilla Developer Network es: "Spread syntax allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected."

Lo que quiere decir que este operador distribuye los elementos dentro de un iterable (cadena de texto, array o cualquier cosa que se pueda recorrer) dentro de un receptor. En otras palabras se usa para expandir objetos iterables como *arrays* en elementos individuales y nos permite fusionar, copiar o pasar elementos por parámetro en funciones sin tener que iterar a través de ellos, sin que se modifique el objeto o variables originales. Veamos las funcionalidades principales.

**Concatenar Arrays**
```javascript
const coleccion1 = [1, 2, 3];
const coleccion2 = [4, 5, 6];
const concatenatedArr = [...coleccion1, ...coleccion2];
console.log(concatenatedArr) // Resultado: [1, 2, 3, 4, 5, 6]

```
**Copiar estructuras de datos**
```javascript
const original = [1, 2, 3];
const copia = [...original];

``` 
**Pasar argumentos a funciones**
```javascript
const numeros = [15, 5, 7, 2, 9];
const minimo = Math.min(...numeros);
console.log(minimo) // 2
```
**Fusionar objetos**
```javascript
const obj1 = {a: 1, b: 2};
const obj2 = {c: 3, d: 4};
const combinado = {...obj1, ...obj2};
console.log(combinado) // {a: 1, b: 2, c: 3, d: 4}
```

## Programación orientada a objetos con JS

<p><img width="1164" height="525" alt="POO_JS" src="https://github.com/user-attachments/assets/afe01f15-6832-4576-9cf7-11beaab5f78f" /></p>


Históricamente un programa era visto como un conjunto de procesos lógicos que, a partir de unos datos de entrada, se procesaban y producían unos datos de salida. La programación orientada a objetos utiliza “objetos” (estructuras de
datos y métodos) y sus interacciones para diseñar aplicaciones. En este paradigma, cada objeto debe ser visto como una entidad con una serie de propiedades que le hacen único y que es responsable de realizar una serie de procesos
(métodos) para los que ha sido creado, basándose un patrón o tipo común para todos los objetos de su misma clase.

JavaScript implementa los cuatro principios básicos de la programación orientada a objetos: abstracción, encapsulación, herencia y polimorfismo, pero, a diferencia de otros lenguajes como Java, es posible programar sin necesidad de utilizar exclusivamente estas características.

Hasta hace unos años, JavaScript NO era un lenguaje orientado a objetos, por tanto no tenía clases, y como cada función en JavaScript es un objeto y los objetos pueden tener atributos, los desarrolladores comenzaron a agregar atributos a las funciones como si fueran objetos normales, lo que les permitió tratarlas como una clase.

JavaScript es un lenguaje con muchas excepciones, por ello es difícil de aprender para muchas personas, pero si entendemos que prácticamente todo en JavaScript es un objeto al que podemos añadir atributos, funciones y demás, entonces es mucho más sencillo entender cómo funciona.

En POO hay varios conceptos básicos, que de forma muy esquemática, son:

*Clase*: Es el molde, o el patrón que define qué propiedades y métodos va a tener un objeto que sea una instancia de la esta clase. Primero hay que **instanciar** la clase para convertirla en un objeto. La instanciación se hace con el constructor `this`. Una vez que es un objeto, se puede hacer lo que se necesite con él. 

<p><img width="777" height="536" alt="class-object" src="https://github.com/user-attachments/assets/806446d7-df6b-4aa4-bb6e-daf44f48158f" /></p>


```javascript
// Definición de la clase
 class Persona {
 constructor(nombre, edad) {
 this.nombre = nombre;
 this.edad = edad;
 }

// Método de la clase

 saludar() {
 console.log(`Hola, me llamo ${this.nombre} y tengo ${this.edad} años.`);

 }
}

 // Creación de objetos

const persona1 = new Persona('Juan', 30);
const persona2 = new Persona('Ana', 25);

// Uso de los métodos del objeto
persona1.saludar(); // Hola, me llamo Juan y tengo 30 años.
persona2.saludar(); // Hola, me llamo Ana y tengo 25 años.

```

*Herencia*: Nos permite crear una subclase(clase hija) que posea automáticamente las propiedades y métodos de la superclase o clase padre. De forma que reutilizamos código.

 ```javascript
 class Animal {
 constructor(nombre) {
 this.nombre = nombre;
 }

 hacerSonido() {
 console.log('El animal hace un sonido');
 }
}

```
  
*Polimorfismo*: Podemos ejecutar un mismo método en objetos distintos sin importar qué tipo tienen porque en cada caso se ejecuta la implementación correcta.

```javascript
// Clase base

class Vehiculo {
 constructor(marca) {
 this.marca = marca;
 }

 acelerar() {
 console.log('El vehículo está acelerando');
 }
}

// Clase derivada

class Coche extends Vehiculo {
 acelerar() { 
 console.log('El coche está acelerando');
 }
}
```

*Encapsulamiento*: Es la capacidad de definir propiedades y métodos privados dentro de un objeto. Que serán únicamente accesibles desde dentro de la función donde se han definido

```javascript
class Student extends Person {
  #year;

  constructor(name, year) {
    super(name);
    this.#year = year;
  }

  introduceSelf() {
    console.log(
      `¡Hola! me llamo ${this.name} y estoy en el año ${this.#year}.`,
    );
  }

  canStudyArchery() {
    return this.#year > 1;
  }
}
```
En este ejemplo `year` es una propiedad de dato privada. Podemos crear un objeto Student que puede acceder a la propiedad #year internamente, sin embargo, si algún código que se encuentre afuera de la clase intenta acceder a la propiedad #year, el navegador lanzará un error. Las propiedades de datos privadas deben ser declaradas en la propia declaración de la clase y sus nombres deben empezar con #.

**Ejes esenciales del desarrollo actual**

La POO en JavaScript no se trata solo de crear estructuras, sino de aplicar *buenas prácticas* para que el código sea escalable y fácil de mantener.

- Módulos (ES Modules): Esenciales para la arquitectura moderna. Permiten dividir el código en múltiples archivos (usando import y export), organizando las clases de manera modular y facilitando el trabajo en equipo.
- Patrones de diseño: La aplicación de principios como SOLID ayuda a crear software más robusto y preparado para el crecimiento.
- Integración de Paradigmas: Un entorno moderno exige saber cuándo usar orientación a objetos y cuándo optar por programación funcional, logrando un código mucho más limpio.

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

