# solid-principles

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

pero ¿ Qué pasa cuando tengo más de una clase? que pasa cuando tengo muchas acciones, a medida que mi code crece el programa se vuelve más y más grande, es importante organizarlo bien y tener un criterio del tamaño y las acciones de mis clases y la interacción de unas con otras, como esto es algo que muchas personas necesitan hacer,se crearón unos principios, 'los principios de la programación orientada a objetos' 


## **`S`** - **Principio de Responsabilidad Única (Single Responsibility Principle - SRP)**.
 
    
   Una clase debe tener **una sola razón para cambiar**. Es decir, cada clase debe hacer solo una cosa. cada clase debe dedicarse a una única cosa.
    
  Ejemplo Orquesta: cada músico toca un solo instrumento no varios, es su única responsabilidad.
    
  Ejemplo app calculadora: No combines la lógica de impresión con la lógica de cálculos en una misma clase.

  Ejemplo sobre el code:
  

  ```  
❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌❌
Atención: Ejemplo SIN la S de solid, a continuación vamos a ver una clase que tiene demasiadas responsabilidades
  ```   
  ```
  //❌ Clase->responsabilidad:representar al usuario, manejar la autenticación, manejar la actualización del perfil

    class User {
      constructor(public username: string, public password: string, public email: string) {}
    
      register() {
        console.log(`Registrando usuario: ${this.username}`);
      }
    
      login() {
        console.log(`Autenticando usuario: ${this.username}`);
      }
    
      updateProfile(email: string) {
        this.email = email;
        console.log(`Actualizando email de ${this.username} a ${this.email}`);
      }
    }
    
    const user = new User("juanita123", "password123", "juanita@example.com");
    user.register();
    user.login();
    user.updateProfile("nuevoemailjuanita@example.com");
 ```
  
     ✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅
      Atención: Ejemplo CON la S de solid, a continuación vamos a ver clases con una única responsabilidad
 ```
      // ✅ Clase->responsabilidad: representa solo al usuario
      class User {
        constructor(public username: string, public password: string, public email: string) {}
      }
      
      // ✅ Clase->responsabilidad:  manejar la autenticación
      class AuthService {
        login(user: User) {
          console.log(`Autenticando usuario: ${user.username}`);
        }
      
        register(user: User) {
          console.log(`Registrando usuario: ${user.username}`);
        }
      }
      
      // ✅Clase->responsabilidad: manejar la actualización del perfil del usuario
      class UserProfileService {
        updateEmail(user: User, newEmail: string) {
          user.email = newEmail;
          console.log(`Email actualizado a: ${user.email}`);
        }
      }
      
 
      const user = new User("juan123", "password123", "juan@example.com");
      const authService = new AuthService();
      const profileService = new UserProfileService();
      
      authService.register(user);
      authService.login(user);
      profileService.updateEmail(user, "nuevoemail@example.com");

  ```



