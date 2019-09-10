

## Lista de Alumnos 

| Apellido(s)           | Repositorio                                |
| ----------------------|--------------------------------------------|
| Silva                 | [Luissf1](https://github.com/Luissf1/POO)  |
| Trujillo              | [kikhi](https://github.com/kikhi/POO)      |
| De Luna               | [Rodrigo-deluna](https://github.com/Rodrigo-deluna)|
| Espinoza Ruiz         | [pabloalber84](https://github.com/pabloalber84)|
| Paniagua  Gutierrez   | [CarlosGtzOf](https://github.com/CarlosGtzOf)|
| Rodolfo Hernandez     | [Rodolfo-hernandez1](https://github.com/Rodolfo-hernandez1/CursoOOP)  |
| Lozano Alvarez        | [zefra](https://github.com/zefra/p.oo)      |
| Flores Velez          | [ernestoramflovlz](https://github.com/ernestoramflovlz/Poo)|
| Leon                  | [FelixELM](https://github.com/FelixELM/POO)|
| López Roblero         | [CesarHLR](https://github.com/CesarHLR/POO)|
| Jairo Perez           | [jairo570](https://github.com/jairo570/POO)|
| Mauricio Chavez       | [Mauricio2110](https://github.com/Mauricio2110/Poo)|
| Christian Martinez    | [ChrisHomeless](https://github.com/ChrisHomeless/HomelessPOO)|
| Marco Rivera          | [MarcoRivera21](https://github.com/MarcoRivera21/Marco-Rivera/blob/master/README.md)|
| Saul Valadez          | [saulvaladez18](https://github.com/saulvaladez18/ShaggyPOO)|
| Lopez Esquerra        | [PhantompD](https://github.com/PhantompD/OOP)|
| DigitalSnakedotexe    | [DigitalSnakedotexe](https://github.com/DigitalSnakedotexe/POO)|
| Quintero Montalvo     | [luisqm](http://github.com/luisqm/POO)|
| García Gabriel        | [GarciaG1](https://github.com/GarciaG1/POO1)|
| Medina                | [M3D1N4](https://github.com/M3D1N4/Dorya-poo)|


# Actividades 

Fechas de entrega son en horario local de Tijuana.

## Crear Repositorio en Github (10 de Septiembre 9:00 horas) 

1. Debes crear una cuenta en GitHub e instalar git localmente.
2. Crea un repositorio público llamado POO. Agrega los archivos *.gitignore* y *README.md*.
3. Incluye una portada en el archivo README.md. Este archivo será la portada e índice de tus evidencias. Debes agregar vínculos a las actividades del curso. Debes organizar el portafolio utilizando subdirectorios.
4. Envía un correo o mensaje al profesor con tu nombre completo y usuario de GitHub.

5. **Opcional** Haz un fork de este repositorio y agrega tu mismo el nombre a este archivo, solicita un pull request para que se actualize.

Crear un repositorio  [GitHub Help](https://help.github.com/en/articles/create-a-repo)   
Crear un pull request [GitHub Help](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork)


## Ejercicio de Markdown en Github (12 de Septiembre 9:00 horas)

Crea un nueva carpeta en el repositorio *POO* llamada *Setup* la cual incluya un archivo *README.md*   En el cual se describan los pasos para instalar el ambiente de desarrollo para aplicaciones de consola en C#. Debes de utilizar imágenes,hipervínculos a archivos dentro de tu repositorio. Se deben incluir detalles de:

1. Instalación de dotnet core 2.2.
2. Instalación y configuración de Visual Studio Code para C#.
3. Instalación de git. conectado a tu cuenta de GitHub y VSC.

[Documento de Apoyo](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Programa básico Películas (13 de Septiembre 9:00 horas)

De acuerdo a los ejemplos vistos en clase y la lectura. Implementa en c# la clase *Pelicula*  con los siguientes atribitos **publicos**:


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

## Lista de Películas (15 de Septiembre 9:00 horas)

Utilizando la bibliteca *System.Collections.Generic* crea una lista de 5 peliculas. Utilizando la lista genérica **List<Pelicula>**.
1. Crea la lista en *Main()* y agrega directamente las peliculas a la lista, por ejemplo para la clase Personasería de esta manera (fragmento):

```csharp
List<Persona> personas = new List<Persona>();

persona.Add(new Persona ("pam"));
persona.Add(new Persona ("tom"));
persona.Add(new Persona ("jim"));

```
2. Utiliza un ciclo **foreach** para iterar por la lista e imprimir las peliculas.

## Actores (16 de Septiembre 9:00 horas)

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
