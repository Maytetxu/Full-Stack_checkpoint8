---
title: Operador de extensión en JS
nav_order: 6
---
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
