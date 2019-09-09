
## Declaración de una clase

Una *clase* nos permite especificar que atributos y comportamiento tendrán los
objetos definidos por ella.

Por ejemplo, si desamos tener objetos tipo *Bicicleta*, debemos definir la 
clase *Bicicleta* con atributos que para nuestro programa representen a una
bicileta:

| atributo             | tipo           |
| ---------------------|----------------|
| marca                | String         |
| color                | String         |
| velocidad_actual     | Int16          |

En la clase también especificamos el comportamiento que tendrán los objetos 
tipo *Bicicleta*. Esto lo hacemos declarando ciertos métodos dentro de la
clase: 

| método                    | tipo-regreso   | argumentos     | descripción                                     |  
| --------------------------|----------------|----------------|-------------------------------------------------|
| imprime()                 | void           |                | imprime en consola el estado actual del objeto  |
| velocidad_actual()        | Int16          |                | velocidad actual de la bicicleta                |
| incrementa_velocidad()    | void           |                | incrementa la velocidad actual de la bicicleta  |


En C# le damos el nombre de **métodos instancia**, a estos métodos, ya que no
tiene sentido llamar al método **imprime()** si no está asociado a un objeto.
Primero debemos crear un objeto, para luego pedirle que imprima sus datos. 

Una clase es un contenedor donde especificamos aquellos atributos y métodos 
que hemos decidido tendrán un nuevo tipo de objetos. 

Decimos que una clase es una **abstracción**, por que nos permite primero   
seleccionar que atributos y métodos nos interesa que tengan nuestras bicicletas 
para una aplicación determinada. Por ejemplo, en este caso ignoramos
atributos como el precio, altura del asiento, etc. que en otras aplicaciones
podrían ser importantes. También podemos utilizar y pensar en los objetos tipo 
bicicleta sin entrar en detalles de como se programó el método *imprime()* o
**incrementa_velocidad()**.

Vamos a definir una nueva clase. Empezamos por declarar un nuevo contenedor 
o bloque **{ }**, especificando antes que es una clase y dándole un nombre:

```csharp
class Bicicleta
{

} 
```

El bloque **{ }** es *muy* importante, en este caso está vacio. Vamos a 
agregar dentro del bloque algunos atributos:

```csharp
class Bicicleta
{
  public String marca;
  public String color;
  public Int16 velocidad_actual;  
} 
```

Listo, hemos especificado que atributos tendrán nuestras bicicletas, aunque
no tengan ningún comportamiento todavía. Vamos a *instanciar* o crear objetos
del tipo *Bicicleta*. Esto lo vamos hacer dentro del método **Main()** de la clase
**Program**.


```csharp
using System;
using System.Collections.Generic;

class Bicicleta
    {
        public String marca;
        public String color;
        public Int16 velocidad_actual;  
    } 

 class Program
    {
        static void Main(string[] args)
        {
            Bicicleta bici = new Bici();        
            bici.marca = "Huffy";
            bici.color = "Rojo";
            bici.velocidad_actual = 2;
            
            Console.WriteLine("Marca:{0}, Color:{1}, Velocidad actual:{2}",bici.marca, bici.color, bici.velocidad_actual );
        }
    }

```






