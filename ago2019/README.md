

## Lista de Alumnos 

| Nombre             | Repositorio                                | 
| -------------------|--------------------------------------------|
|AGUAYO AGUAYO YAEL  | [Yaguay](https://github.com/Yaguay/POO)| 
|ALEMAN URETA ENRIQUE  | [EchoWitcher](https://github.com/EchoWitcher/POO)| 
|ANGULO GOMEZ CRISTO ABELARDO | | 
|CHAVEZ ARROYO MAURICIO | [Mauricio2110](https://github.com/Mauricio2110/Poo)|
|CHAVEZ TRINIDAD RUBEN FELIX  | [rwb3x](https://github.com/rwb3x/POO)|
|DE LUNA CORRAL JESUS RODRIGO | [Rodrigo-deluna](https://github.com/Rodrigo-deluna)|
|DIAZ CORONA ASHLEY YEDITH | | 
|ESPINOZA RUIZ PABLO ALBERTO  | [pabloalber84](https://github.com/pabloalber84)|
|FLORES VELEZ ERNESTO RAMSES | [ernestoramflovlz](https://github.com/ernestoramflovlz/POO.)|
|GARCIA LARES MIGUEL ANGEL  | [Miguel2496](https://github.com/Miguel2496/OOP-MI)|
|GARCIA PEREZ GABRIEL  | [GarciaG1](https://github.com/GarciaG1/POO1)|
|GUERRERO AGUILAR ELIGIO GUADALUPE  | [EligioGA](https://github.com/EligioGA/POO)|
|GUTIERREZ LOZANO JUAN PABLO  | [DigitalSnakedotexe](https://github.com/DigitalSnakedotexe/POO)|
|HERNANDEZ QUIROZ RODOLFO IVAN  | [Rodolfo-hernandez1](https://github.com/Rodolfo-hernandez1/CursoOOP)  |
|JIMENEZ GONZALEZ MANUEL| 
|LEON MOLINA FELIX ENRIQUE  | [FelixELM](https://github.com/FelixELM/POO)|
|LOPEZ ESQUERRA JONATHAN DANIEL  | [PhantompD](https://github.com/PhantompD/OOP)| 
|LOPEZ ROBLERO CESAR HUMBERTO  | [CesarHLR](https://github.com/CesarHLR/POO)|
|LOZANO ALVAREZ MARCO POLO  | [zefra](https://github.com/zefra/p.oo) | 
|LUIS CASTILLO VALERIA | [valeria1703](https://github.com/valeria1703/POO)|
|MARTINEZ MURRIETA CHRISTIAN ANDRES  | [ChrisHomeless](https://github.com/ChrisHomeless/HomelessPOO)|
|MEDINA MAGAÑA HECTOR MANUEL | [M3D1N4](https://github.com/M3D1N4/Dorya-poo)|
|MERCADO CRUZ ARTURO  | [Arturo-M](https://github.com/Arturo-M/OOP)|
|ORDAZ MEDINA RICARDO DANIEL|  |
|PAEZ RENTERIA DAVID ARMANDO  | [foxsok](http://github.com/foxsok)|
|PANIAGUA GUTIERREZ CARLOS ADRIAN | [CarlosGtzOf](https://github.com/CarlosGtzOf)|
|PEREZ ROJAS JAIRO JAZIEL | [jairo570](https://github.com/jairo570/POO)|
|PICOS QUEZADA ERICK DANIEL| |
|PORTUGAL QUINTERO ADOLFO | [4DownPortu](https://github.com/4DownPortu/POO)|
|QUINTERO MONTALVO LUIS ENRIQUE | [luisqm](http://github.com/luisqm/POO)|
|RAMIREZ CORONEL ALBERTO | [AlbertoRaCa](https://github.com/AlbertoRaCa/OOP)|
|REYES CARO MARCO ANTONIO | [marcoreyes666](https://github.com/marcoreyes666/POO)|
|RIVERA MARTINEZ MARCO ANTONIO | [MarcoRivera21](https://github.com/MarcoRivera21/Marco-Rivera/blob/master/README.md)|
|RUIZ VILLEGAS JAVIER YOEL | [YoelRuiz](https://github.com/YoelRuiz)|
|SILVA REYES LUIS ADRIAN | [Luissf1](https://github.com/Luissf1/POO)  |
|TECUAPA GALLARDO ARTURO | [ArturoTecuapa50](https://github.com/ArturoTecuapa50)|
|TEJEDA COTA ERICK  | [iwanttacos](https://github.com/iwanttacos/POO)|
|TRUJILLO GARAY CESAR ANDRES | [kikhi](https://github.com/kikhi/POO)      |
|VALADEZ CORRALES SAUL ALEJANDRO | [saulvaladez18](https://github.com/saulvaladez18/ShaggyPOO)|

# Actividades 

** También pueden hacer pull-request siguiendo las instrucciones adicionales en el [repositorio correspondiente](https://github.com/mariosky/EjerciciosOPP).


## Clases Abstractas   (24 de Octubre)

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

## Herencia   (23 de Octubre) 
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

## Sobrecargado de Operadores, ejercicios en clase   (23 de Octubre) 
### Duración
Implementa la clase **Duración** siguiendo los pasos:

1. Declara la clase **Duración** con los atributos: *horas*, *minutos* y *segundos*. Estos atributos puden ser propiedades. Por ejemplo, pudes guardar todo en segundos y calcular como paramentres las *horas* y *minutos*. Implementa un método para imprimir la duración en el formato *HH:MM:SS*.
2. Sobrecarga el constructor **Duración(int h, int m, int s)**.
2. Sobrecarga el constructor **Duración(int segundos)**. Dependiendo de la implementación del paso 1, puede ser que debas extraer las horas y los minutos.
3. Sobrecarga el operador **+** para que puedas sumar dos objetos tipo **Duración**. 

### Dominó
Implementa la clase **Domino** siguiendo los pasos:

1. Declara la clase **Domino** con los atributos: *Espacio1* y *Espacio2*.
2. Sobrecarga el operador **+** para que puedas sumar dos objetos tipo **Domino**. El resultado debe ser un entero, con la suma de los puntos de ambas piezas.

## Paso de parámetros (30 de Septiembre) 

1. Lee el texto de [pase de parametros](../clases/params.md).
1. Escribe un programa en el cual ejemplifiques el paso de parámetros
**por valor** y **por referencia** utilizando los modificadores **ref**, **out** e **in**.


## Crear Repositorio en Github (18 de Septiembre) 

1. Debes crear una cuenta en GitHub e instalar git localmente.
2. Crea un repositorio público llamado POO. Agrega los archivos *.gitignore* y *README.md*.
3. Incluye una portada en el archivo README.md. Este archivo será la portada e índice de tus evidencias. Debes agregar vínculos a las actividades del curso. Debes organizar el portafolio utilizando subdirectorios.
4. Envía un correo o mensaje al profesor con tu nombre completo y usuario de GitHub.

5. **Opcional** Haz un fork de este repositorio y agrega tu mismo el nombre a este archivo, solicita un pull request para que se actualize.

Crear un repositorio  [GitHub Help](https://help.github.com/en/articles/create-a-repo)   
Crear un pull request [GitHub Help](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork)


## Ejercicio de Markdown en Github (19 de Septiembre)

Crea un nueva carpeta en el repositorio *POO* llamada *Setup* la cual incluya un archivo *README.md*   En el cual se describan los pasos para instalar el ambiente de desarrollo para aplicaciones de consola en C#. Debes de utilizar imágenes,hipervínculos a archivos dentro de tu repositorio. Se deben incluir detalles de:

1. Instalación de dotnet core 2.2.
2. Instalación y configuración de Visual Studio Code para C#.
3. Instalación de git. conectado a tu cuenta de GitHub y VSC.

[Documento de Apoyo](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Programa básico Películas (20 de Septiembre)

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

## Lista de Películas (21 de Septiembre)

Utilizando la bibliteca *System.Collections.Generic* crea una lista de 5 peliculas. Utilizando la lista genérica **List<Pelicula>**.
1. Crea la lista en *Main()* y agrega directamente las peliculas a la lista, por ejemplo para la clase **Persona** sería de esta manera (fragmento):

```csharp
List<Persona> personas = new List<Persona>();

persona.Add(new Persona ("pam"));
persona.Add(new Persona ("tom"));
persona.Add(new Persona ("jim"));

```
2. Utiliza un ciclo **foreach** para iterar por la lista e imprimir las peliculas.

## Actores (22 de Septiembre)

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

