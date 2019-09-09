

## Lista de Alumnos 

| Apellido(s)          | Repositorio                                |
| ---------------------|--------------------------------------------|
| Silva                | [Luissf1](https://github.com/Luissf1/POO)  |
| Trujillo             | [kikhi](https://github.com/kikhi/POO)      |
| De Luna              | [Rodrigo-deluna](https://github.com/Rodrigo-deluna)|


## Actividades Iniciales

Fechas de entrega son en horario local de Tijuana.

# Crear Repositorio en Github (Fecha de ENTREGA: 10 de Septiembre 9:00 horas)

1. Debes crear una cuenta en GitHub e instalar git localmente.
2. Crea un repositorio público llamado POO. Agrega los archivos *.gitignore* y *README.md*.
3. Incluye una portada en el archivo README.md. Este archivo será la portada e índice de tus evidencias. Debes agregar vínculos las actividades del curso. Debes organizar el portafolio utilizando subdirectorios.
4. Envía un correo o mensaje al profesor con tu nombre completo y usuario de GitHub.

5. **Opcional** Haz un fork de este repositorio y agrega tu mismo el nombre a este archivo, solicita un pull request para que se actualize.

Crear un repositorio  [GitHub Help](https://help.github.com/en/articles/create-a-repo)   
Crear un pull request [GitHub Help](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork)


# Ejercicio de Markdown en Github (Fecha de ENTREGA: 12 de Septiembre 9:00 horas)

Crea un nueva carpeta en el repositorio *POO* llamada *Setup* la cual incluya un archivo *README.md*   En el cual se describan los pasos para instalar el ambiente de desarrollo para aplicaciones de consola en C#. Debes de utilizar imágenes,hipervínculos a archivos dentro de tu repositorio. Se deben incluir detalles de:

1. Instalación de dotnet core 2.2.
2. Instalación y configuración de Visual Studio Code para C#.
3. Instalación de git. conectado a tu cuenta de GitHub y VSC.


# Programa básico orientado a objetos (Fecha de ENTREGA: 13 de Septiembre 9:00 horas)

De acuerdo a los ejemplos vistos en clase y la lectura. Implementa en c# la clase *Pelicula*  con los siguientes atribitos **publicos**:


### Pelicula
| atributo             | tipo           |
| ---------------------|----------------|
| titulo               | String         |
| año                  | Int16          |
| país                 | String         |
| director             | String         |

1. Como primer paso crea solo la clase con los atribitos públicos e inicializalos en **Program.Main()**.
2. Crea dos objetos tipo Pelicula con dos peliculas ganadoras de un Oscar. 
3. Imprime en la consola el titulo y año de las peliculas. 
Sube la primera versión a GitHub.
4. Ahora cambia los atributos a **private**. Agrega los métodos necesarios para crear los objetos de la siguiente manera:

```csharp
class Program 
{
static void Main(){

    Pelicula p1 = new Pelicula():
    p1.SetTitulo("La La Land");
    p1.SetAño(2016); 
    Console.WriteLine("{0}({1})", p1.GetTitulo(), p1.GetAño());

}
} 
```
Actualiza la versión a GitHub.

5. Por último agrega dos constructores: *Pelicula()* y *Pelicula(string titulo, Int16 año )* y el método imprime();
Actualiza la versión a GitHub.


