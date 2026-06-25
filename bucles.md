---
title: Tipos de bucles en JavaScript
nav_order: 2
---
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
