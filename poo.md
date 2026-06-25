---
title: Programación orientada a objetos con JS
nav_order: 7
---
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
