---
title: const, let y var - Diferencias y usos
nav_order: 3
---
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
