# SOLID-principles

Los principios SOLID son cinco reglas **para escribir código limpio y bien estructurado** enfocado en la programación orientada a objetos. 
Su objetivo es hacer que el software sea más fácil de entender, mantener y escalar. 

```
💬 En pocas palabras:
 SOLID te ayuda a escribir código que no se rompa fácilmente y que sea más fácil de entender y modificar
```

Cada una de las letras hace referencia a un principio 1.`S` 2.`O` 3.`L` 4.`I` 5.`D`

  >_*aclaración🙋‍♀️:aunque se crearon pensando en la programación orientada a objetos también es posible aplicarlos en otros paradigmas como el funcional._

Pero antes de todo preguntémonos… **¿qué es la Programación Orientada a Objetos?**
```
La Programación Orientada a Objetos (POO) es una forma de escribir programas que se basa en organizar el código en objetos.
```

Muy bien y...**¿Cómo organizo mi código con POO?** 👉 con clases.

Cuando empiezo a escribir mi código, lo organizo a través de clases. Estas clases son como moldes que me permiten crear objetos y definir las acciones que pueden hacer (eso que llamamos métodos).

Este es el nivel más básico👶:

>👶Tengo clases,

>👶Las clases pueden crear objetos,

>👶Y esos objetos pueden hacer cosas.


Ahora bien… ¿qué pasa cuando tengo más de una clase? **¿Y si tengo muchas acciones, muchas responsabilidades?** 

A medida que mi código crece, el programa se vuelve más complejo. Por eso es tan importante tener un criterio claro para organizarlo bien:

¿Qué tan grande debe ser una clase? ¿Cuántas cosas debería hacer?¿Cómo deberían interactuar entre ellas?

Como esto es algo que muchas personas del mundo del desarrollo enfrentan, se definieron principios a seguir para ayudar a tomar buenas decisiones.
````
💡Personas viendo problemas y buscando soluciones💡
````

Así nacieron los principios de la programación orientada a objetos: los principios SOLID.

> 🔴✋ _Ojo: no hay que confundirlos con los PILARES de la programación orientada a objetos (abstracción, encapsulamiento, herencia y polimorfismo), que son los conceptos base de cómo funciona este paradigma._
<br/>

`IMPORTANTE`👇
---

---
`PILARES VS PRINCIPIOS`
>Los pilares son el **"cómo funciona la POO"**
>
>SOLID es el **"cómo escribir buen código con POO".**
---
  <img src='./PILARES_VS_PRINCIPIOS.png'/>

`Comenzamos con los principios SOLID`
---

## **`S`** - **Principio de Responsabilidad Única**.

 
¿Qué significa que una clase tenga una “responsabilidad única”?

Significa que una clase debe encargarse de una sola cosa.En otras palabras: una clase debe tener un solo motivo para cambiar.
Ejemplo en la vida real: en una orquesta cada músico toca un solo instrumento no varios, es su única responsabilidad.
Ejemplo sobre el code: Vamos hacer nuestra clase Libro para nuestra app de libros

Si mi app es de libros, la clase libros tendrá mucha responsabilidad, como organizo mi code?
Si yo no supiera de los principios SOLID podría acabar haciendo algo como esto:

  
`❌Atención❌: Ejemplo SIN ❌ la S de solid, a continuación vamos a ver una clase que tiene demasiadas responsabilidades`   

  ```
class Book {
  title: string;
  author: string;

    constructor(title: string, author: string) {
      this.title = title;
      this.author = author;
    }
  
    displayInfo() {
      console.log(`${this.title} - ${this.author}`);
    }
  
    saveToDatabase() {
      // logic to save the book to a database
    }
  
    exportAsPDF() {
      // logic to export the book as a PDF
    }
}

```

¿Qué problema vemos aquí?
La clase Libro está haciendo más de una cosa: tiene demasiadas responsabilidades


> 1️⃣Representa los datos del libro + 2️⃣Muestra información en consola  + 3️⃣Guarda en la base de datos + 4️⃣Exporta como PDF 

Si mañana cambiamos la forma de guardar libros, esta clase cambiaría. Si mañana cambiamos el formato del PDF, también cambiaría.
Demasiados motivos para cambiar...no estamos siguiendo el primer principio y eso a lar larga nos traerá problemas.

**¿Cómo lo solucionamos? Separando las responsabilidades** en clases distintas, es decir, siguiendo el primer principio.

 ` ✅Atención ✅: Ejemplo ✅ CON la S de solid, a continuación vamos a ver clases con una única responsabilidad`   

  
 ```
class Book {
  title: string;
  author: string;

    constructor(title: string, author: string) {
      this.title = title;
      this.author = author;
    }
  }
  
  class BookPrinter {
    displayInfo(book: Book) {
      console.log(`${book.title} - ${book.author}`);
    }
  }
  
  class BookService {
    save(book: Book) {
      // logic to save to the database
    }
  }
  
  class BookPDFExporter {
    export(book: Book) {
      // logic to export as PDF
    }
  }

  ```

Este code en un repositorio lo encontrarías ordenado por carpetas

la clase Book: 📁 models/Book.ts

la clase BookServices 📁 services/BookService.ts

la clase BookPrinter 📁 utils/BookPrinter.ts




