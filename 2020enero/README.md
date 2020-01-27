

## Lista de Alumnos 

| Nombre             | Repositorio                                | 
| -------------------|--------------------------------------------|
| Nombre del Alumno  | [Usuario](https://github.com/)| 


# Actividades 
También pueden hacer pull-request siguiendo las instrucciones adicionales en el [repositorio correspondiente](https://github.com/mariosky/EjerciciosOPP).


## Crear Repositorio en Github  

1. Debes crear una cuenta en GitHub e instalar git localmente.
2. Crea un repositorio público llamado POO. Agrega los archivos *.gitignore* y *README.md*.
3. Incluye una portada en el archivo README.md. Este archivo será la portada e índice de tus evidencias. Debes agregar vínculos a las actividades del curso. Debes organizar el portafolio utilizando subdirectorios.
4. Envía un correo o mensaje al profesor con tu nombre completo y usuario de GitHub.

5. **Opcional** Haz un fork de este repositorio y agrega tu mismo el nombre a este archivo, solicita un pull request para que se actualize.

Crear un repositorio  [GitHub Help](https://help.github.com/en/articles/create-a-repo)   
Crear un pull request [GitHub Help](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork)


## Ejercicio de Markdown en Github 
Crea un nueva carpeta en el repositorio *POO* llamada *Setup* la cual incluya un archivo *README.md*   En el cual se describan los pasos para instalar el ambiente de desarrollo para aplicaciones de consola en C#. Debes de utilizar imágenes,hipervínculos a archivos dentro de tu repositorio. Se deben incluir detalles de:

1. Instalación de dotnet core 2.2.
2. Instalación y configuración de Visual Studio Code para C#.
3. Instalación de git. conectado a tu cuenta de GitHub y VSC.

[Documento de Apoyo](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Programa básico Películas 

De acuerdo a los ejemplos vistos en clase y la lectura. Implementa en c# la clase *Pelicula*  con los siguientes atributos **publicos**:


### Pelicula
| atributo             | tipo           |
| ---------------------|----------------|
| titulo               | String         |
| año                  | Int16          |
| país                 | String         |
| director             | String         |


1. Como primer paso crea solo la clase con los atributos públicos e inicializalos en **Program.Main()** directamente.
2. Crea dos objetos tipo Pelicula con dos peliculas ganadoras de un Oscar. 
3. Imprime en la consola el titulo y año de las peliculas. 
Sube la primera versión a GitHub.
4. Ahora cambia los atributos a **private**. Agrega los métodos necesarios para crear los objetos de la siguiente manera:

```csharp
class Program 
{
static void Main(){

    Pelicula p1 = new Pelicula();
    p1.SetTitulo("La La Land");
    p1.SetAño(2016); 
    Console.WriteLine("{0}({1})", p1.GetTitulo(), p1.GetAño());

}
} 
```
Actualiza la versión a GitHub.

5. Por último agrega dos constructores: *Pelicula()* y *Pelicula(string titulo, Int16 año )* y el método imprime().
Actualiza la versión a GitHub.

## Lista de Películas 

Utilizando la bibliteca *System.Collections.Generic* crea una lista de 5 peliculas. Utilizando la lista genérica **List<Pelicula>**.
1. Crea la lista en *Main()* y agrega directamente las peliculas a la lista, por ejemplo para la clase **Persona** sería de esta manera (fragmento):

```csharp
List<Persona> personas = new List<Persona>();

persona.Add(new Persona ("pam"));
persona.Add(new Persona ("tom"));
persona.Add(new Persona ("jim"));

```
2. Utiliza un ciclo **foreach** para iterar por la lista e imprimir las peliculas.

## Actores 
Agrega a tu clase **Pelicula** un atributo **actores** de tipo **List<Actor>**
Tu clase debe permitir el siguiente funcionamiento:

```csharp
class Program 
{
static void Main(){

    Pelicula p1 = new Pelicula("La La Land", 2016);
    p1.AgregarActor(new Actor("Ryan Gosling", 1980));
    p1.AgregarActor(new Actor("Emma Stone", 1988));

    p1.ImprimeActores();

}
} 
```
## Paso de parámetros  

1. Lee el texto de [pase de parametros](../clases/params.md).
1. Escribe un programa en el cual ejemplifiques el paso de parámetros
**por valor** y **por referencia** utilizando los modificadores **ref**, **out** e **in**.

### Dominó
Implementa la clase **Domino** siguiendo los pasos:

1. Declara la clase **Domino** con los atributos: *Espacio1* y *Espacio2*.
2. Sobrecarga el operador **+** para que puedas sumar dos objetos tipo **Domino**. El resultado debe ser un entero, con la suma de los puntos de ambas piezas.

## Sobrecargado de Operadores, ejercicios en clase   (23 de Octubre) 
### Duración
Implementa la clase **Duración** siguiendo los pasos:

1. Declara la clase **Duración** con los atributos: *horas*, *minutos* y *segundos*. Estos atributos puden ser propiedades. Por ejemplo, pudes guardar todo en segundos y calcular como paramentres las *horas* y *minutos*. Implementa un método para imprimir la duración en el formato *HH:MM:SS*.
2. Sobrecarga el constructor **Duración(int h, int m, int s)**.
2. Sobrecarga el constructor **Duración(int segundos)**. Dependiendo de la implementación del paso 1, puede ser que debas extraer las horas y los minutos.
3. Sobrecarga el operador **+** para que puedas sumar dos objetos tipo **Duración**. 



## Herencia   
### Alumnos
Debes hacer un programa dónde utilices la siguiente jerarquía de clases: **Alumno**, **Licenciatura**,
y **Posgrado**. La diferencia entre un alumno de Licenciatura y de Posgrado es que los alumnos de 
Licenciatrua hacen servicio social y residencias, y el alumno de posgrado tiene un tema de investigación.
Debes:

1. Utilizar herencia. 
2. Utilizar la referencia **base** y miembros de la clase base.
3. Redefinir un método en la clase derivada utilizando el modificador **new**.
4. Prueba la diferencia entre **private** y **protected** para los campos de la clase **Alumno**.

### Músicos
Escribe un programa dónde utilices la siguiente jerarquía de clases: **Músico**, **Baterista**,
**Bajista** y **Guitarrista**. En el método **Main()** debes crear una lista de músicos 
(**List<Músico>**) y utilizando métodos virtuales hacer que los músicos ejecuten los métodos:
**afina()**,**saluda()**,**toca()**. Básate en el ejemplo que vimos en clase. 



## Clases Abstractas  
### Ilustrador
Basándote en el programa que iniciamos en clase (a continuación), términa el programa
utilizando el concepto de clases abstractas.

```csharp
using System;
using System.Collections.Generic;

namespace figura
{
    class Figura 
    {
        protected int x;
        protected int y;
        protected string color;

        public Figura(int x, int y, string c){
            this.x = x; this.y = y; color = c;
        }

        public void dibuja()
        {
            Console.WriteLine("Se dibuja una figura color {0}", 
            color);
        }

        public void printColor() {
            Console.WriteLine(color);
        }
    }

    class Circulo : Figura {
        public Circulo(int x, int y, string c):base(x , y, c){
        }

        public new void dibuja(){
            Console.WriteLine("Se dibuja un circulo {0}", color);
        }
    }

    class Rect : Figura {
        public Rect(int x, int y, string c):base(x , y, c){
            }
        }
    class Program{
        static void Main(string[] args){
            List<Figura> figuras = new List<Figura>();
            figuras.Add(new Circulo(12,13,"verde")) ;
            figuras.Add(new Rect(12,13,"azul")) ;
            figuras.Add(new Rect(12,13,"rojo")) ;
            figuras.Add(new Circulo(12,13,"rojo")) ;
            foreach (var item in figuras){
                item.dibuja();
            }    
            Circulo r = new Circulo(10,10,"rojo");   
            r.dibuja();
            }
        }
}
```

### Músicos Abstractos 
Implementa el programa de **Músico** que hiciste en el tema de Herencia pero con clases abstractas.


## Generics 
### Stack
Implementa la clase **generica** Stack<T>, la cual sea eso una Pila.
Debe incluir los métodos push() y pop() y marcar error en caso de que la pila 
    se desborde o se intente hacer pop() a una pila vacía. Básate en el ejercicio
    visto en clase.
   Prueba tu clase, con varios tipos de dato.
    
### Cola 
    Utilizando las ideas vistas en la clase Stack<T> ahora intenta hacer
    una cola. La cola tiene funciona como FIFO, es decir el primero que
    entra es el primero que sale. Puedes utilizar un arreglo y recorrer los
    elementos como en una fila del mundo real.



