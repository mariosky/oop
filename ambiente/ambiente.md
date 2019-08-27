# Ambiente de desarrollo

## .NET Core
.NET Core es una versión multi-plataforma y de código libre de .NET. Se incluyen bibliotecas para programar sitios web, servicios web y aplicaciones de consola. El lenguaje de programación nativo es C#. 

Como primer paso vamos a instalar el SDK de .NET Core versión 2.2, el cual puedes bajar directamente de [dotnet.microsoft.com](https://dotnet.microsoft.com/download/dotnet-core/2.2). Elige la instalación para tu sistema operativo y arquitectura (64 o 32 bits).

El **framework**, incluye un programa de línea de comandos (en inglés CLI) llamado *dotnet* con el cual vamos a administrar nuestro código y los ejecutables de **.NET**. Vamos a revisar que esté instalado, para esto abre una terminal. En windows se tienen **cmd.exe** y **Power Shell**, en macOS y Linux tenemos la **Terminal**.

Vamos a ver que versiones del  **.NET Core** tenemos instalado en nuestra computadora:

```
dotnet --info
```

Al ejecutar el comando debemos ver un listado de los que tenemos instalado localmente. 

### Comandos de todos los días

#### Crear un proyecto de consola
El comando **dotnet new** ([documentación](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-new?tabs=netcore22)) nos permite crear un nuevo proyecto, archivo de configuración o solución a partir de una plantilla. La plantilla **console** nos permite crear un proyecto tipo consola. Es importante especificar **-o <NOMBRE_PROYECTO>** para que se cree un nuevo directorio llamado **<NOMBRE_PROYECTO>** y se genere el nuevo proyecto dentro de el. El modificador **-o** también se puede indicar como **--output**.  El comando crea dos nuevos directorios **bin** y **obj**, un archivo de configuración **<NOMBRE_PROYECTO>.csproj** y un programa de ejemplo llamado **Program.cs**. 

Vamos a crear un nuevo proyecto dentro del directorio **OOP**, si no haz creado este directorio lo creamos primero y no movemos a el. En Windows:

```
mkdir OOP
cd OOP 
```

Ahora creamos un proyecto llamado **prueba**:

```
dotnet new console -o prueba 
```

El comando nos muestra la siguiente información:

```
The template "Console Application" was created successfully.          

Processing post-creation actions...                                   Running 'dotnet restore' on prueba\prueba.csproj...                   Restore completed in 81.52 ms for 
 D:\OOP\prueba\prueba.csproj.                                     
Restore succeeded.      
```

Vamos a cambiarnos al directorio donde se generó el proyecto. 
Veamos también el contenido del directorio.

```
cd prueba
dir
```
El comando *dir* nos muestra el contenido del directorio:
```
    Directory: D:\OOP\prueba

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         8/27/2019   1:19 PM                obj
-a----         8/27/2019   1:19 PM            188 Program.cs
-a----         8/27/2019   1:19 PM            178 prueba.csproj

```
Podemos ver el programa que se hemos generado con el comando **more**:
```
more .\Program.cs                                                     
```
```
using System;                                                                                            
namespace prueba
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

En la siguiente sección vamos a editar el programa utilizando el editor **Visual Studio Code**, por lo pronto simplemente lo vamos a ejecutar.

#### Compilar y ejecutar un proyecto

Para compilar y ejecutar el programa utilizamos el comando **run**:

```
dotnet run                                                            
```
Vemos como resultado:

```
Hello World!  
```










### Visual Studio Code

### git

### GitHub

## Práctica


