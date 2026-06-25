---
title: Arrow function
nav_order: 4
---
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
