# Paso de parámetros

El paso de parámetros no es un tema exclusivo de la  programación
orientada a objetos, ya que la mayoría de los lenguajes de programación
permiten la definición de [funciones que aceptan parámetros](https://es.wikipedia.org/wiki/Argumento_(inform%C3%A1tica)).
Independientemente del lenguaje que estemos utilizando, es importante 
conocer como se realiza internamente el paso de parámetros, ya que esto
nos permitirá hacer más eficientes nuestros programas.

Para entender bien los conceptos de paso de parámetros en C#,
es importante recordar la diferencia entre los tipos de
variables: [de valor](https://docs.microsoft.com/es-mx/dotnet/csharp/language-reference/keywords/value-types) y [de referencia](https://docs.microsoft.com/es-mx/dotnet/csharp/language-reference/keywords/reference-types).

Cuando ejecutamos un método que requiere parámetros
decimos que le enviamos o pasámos los valores que necesita como argumentos, ya sea de manera
literal o utilizando variables.

Por ejemplo, analizemos este fragmento de código:

```csharp

Duplicador d = new Duplicador();

d.duplica(1);

int x = 2;

d.duplica(x);

```

En el código anterior estamos llamando dos veces al método **duplica(int x)** del
objeto **d**, el método se ha declarado con un parametro  **x** de tipo **int**.  
Al momento de ejecución le pasamos como argumento un entero literal **1**, después una
variable **int x**, inicializada en **2**. La clase **Duplicador** podría estar implementada de 
la siguiente manera: 

```csharp
class Duplicador{

	public void duplica(int n) { 
			n = n*2;
	}

}
```

Por defecto en C# el paso de parámetros se hace **por valor**, 
veamos el concepto en el ejemplo y preguntándonos ¿Qué valor 
tiene **x** al imprimirse?:

```csharp
Duplicador d = new Duplicador();
int x = 2;
d.duplica(x);
Console.WriteLine(x);
```

En el caso de pase **por valor**, **se hace una copia** del objeto que 
se está pasando (en este caso **x**) y 
se guarda localmente en **n**. El hacer una copia tiene un costo adicional 
y además en el caso de que se modifique **n**, (como sucede aquí) este cambio
solo sucederá en la variable local (**n**) y no en el argumento (**x**). En este caso se debe 
imprimir **2**, por lo que ya sabemos. 

Ahora, esto es distinto cuando pasamos variables **tipo referencia**,
veamos otro ejemplo:

```csharp
using System;

class Persona
{
	public string nombre;
	public string apellido;

	public Persona() {
		nombre = 'Fulano';
		apellido = 'De tal';
	}
}

class Anonymous{
	
	static public void anonimiza(Persona p) { 
			p.nombre = 'xxxxxxxxx';
			p.apellido = 'xxxxxxxxx';
	}


	static void Main(){
		Persona espía = new Persona();

		Console.WriteLine(espía.nombre);
		anonimiza(espía);
		Console.WriteLine(espía.nombre);

	}
}
```

Ahora **anonimiza(Persona p)** recibe una referencia al objeto que se envía como 
argumento, en este caso **espía** y se copia a **p**. Esto significa para empezar, que aunque también
se copia el valor, esta copia es una **referencia** al objeto original (argumento). El contar con una referencia 
significa que a diferencia de una variable tipo valor, como en el ejemplo anterior,
ahora **si** podríamos modificar al objeto que recibimos, ya que
tenemos su referencia. ¡Esto puede ser muy peligroso!, aunque como la mayoría 
de las cosas peligrosas, pueden ser benéficas en ciertos casos. 
¿Qué se imprimiría en en el programa anterior?

Veamos como  podemos controlar el comportamiento del pase de parámetros con estas palabras clave:

* *ref* con esta palabra especificamos que el paso de parámetros se hará por referencia incluso cuando las
variables sean de tipo valor. Nos permite modificar el valor del parámetro.

* *in* con esta palabra especificamos que el paso de parámetros se hará por referencia pero evitando que se modifique el parámetro original.

* *out* El objetivo es inicializar el valor de los parámetros y también se pasan por referencia.


## ref 
Vamos a cambiar la implementación del método **incrementa(int n)** del código que vimos anteriormente para ver 
que sucede cuando pasamos un parámetro **tipo valor** con el modificador **ref**. Es solo cuestión de agregar **ref**
al especificar el parámetro:

```csharp
	public void duplica_ref( ref int n) { 
			n*=2;
	}
```

Cuando un parámetro se pasa por referencia, se pasa **directamente** una referencia a la variable externa. Es decir,
No se hace una copia. Esto implica que si se hace un cambio a la variable local, realmente se está haciendo 
el cambio en las dos variables, la local y la externa. 

```csharp
using System;

class Duplicador{

	public void duplica(int n) { 
			n = n*2;
	}

	public void duplica_ref(ref int n) { 
			n = n*2;
	}


}

class Program
{

	static void Main()
	{
		Duplicador d = new Duplicador();
		int x = 2;
		d.duplica(x);
		Console.WriteLine(x);
		d.duplica_ref(x);
		Console.WriteLine(x);
	}
}

```
En este caso, en el llamado a  **d.duplica(x)** no se modifica **x**, pero en **d.duplica_ref(x)**
si se modifica.

¿Qué sucede si enviamos una variable tipo referencia con el modificador **ref**? En este
caso funcionaría **casi** igual, como antes, si modificamos al objeto o variable dentro del método al
ser una copia de la referencia original, se afectaría también a l a variable externa. Recordemos que
la copia se destruye al terminar de ejecutar el método, pero el cambio persiste. 

Vamos a ver un caso especial importante. ¿Qué pasaría si reemplazamos el valor de la referencia dentro del método?
Por ejemplo, en lugar de simplemente anonimizar, ¿que tal si reemplazamos a una persona por otra?, vamos a agregar 
este método a nuestra clase **Anonymous**, con una versión **por valor** y una **por referencia**:

```csharp
class Anonymous{
	
	static public void anonimiza(Persona p) { 
			p.nombre = 'xxxxxxxxx';
			p.apellido = 'xxxxxxxxx';
	}
	static public void cambia(Persona p) { 
			p = new Persona();
			p.nombre = 'John';
			p.apellido = 'Doe';
	}

	static public void cambia_ref( ref Persona p) { 
			p = new Persona();
			p.nombre = 'John';
			p.apellido = 'Doe';
	}

	static void Main(){
		Persona espía = new Persona();

		Console.WriteLine(espía.nombre);
		anonimiza(espía);
		Console.WriteLine(espía.nombre);
		cambia(espía);
		Console.WriteLine(espía.nombre);
		cambia_ref(espía);
		Console.WriteLine(espía.nombre);
	}
}

```

Si ejecutamos el código anterior veremos que el método **cambia(espía)** no reemplaza al objeto **espía**.
Lo hace internamenta en la **copia** de la referencia, pero al terminar el método se destruye. En el caso 
de **cambia_ref(espía)**, como aquí se envia directamente la referencia, si le asignamos un nuevo valor con
**p = new Persona()** se le está asignando también a la variable externa, en este caso **espía**. Por esto,
el programa debería imprimir:

```
Fulano
xxxxxxxxx
xxxxxxxxx
John
```
Cuando enviamos parámetros **por referencia** utilizando **ref** forzosamente deben de estar inicializados,
incluso las variables **tipo valor**. Por ejemplo, esto marcaría error:

```csharp
Duplicador d = new Duplicador();
int x; // Solo estamos declarando x, pero no la inicializamos
d.duplica_ref(ref x); // ERROR
Console.WriteLine(x); 
```
Debemos de inicializar antes:

```csharp
Duplicador d = new Duplicador();
int x = new int(); // También podríamos hacerlo de una manera más común: int x = 4; 
d.duplica_ref(ref x);
Console.WriteLine(x);
```

En este estilo, lo hacemos utilizando un constructor. **TRIVIA:** ¿con que valor se inicializa **x**? 

Otra restricción es que no podemos enviar valores literales:
```csharp
Duplicador d = new Duplicador();
d.duplica_ref(ref 12); //ERROR
Console.WriteLine(x);
```

## out

Aunque no sea muy natural, en ocasiones queremos recibir parámetros **tipo referencia**
con el proposito de modificar o inicializar los valores de los argumentos. 
Veamos un ejemplo, con dos métodos que hacen lo mismo, pero regresan el valor de una manera
distinta:

```csharp
using System;

class Ejemplo {

	static void suma(int a, int b, out resultado){
		resultado = a + b;
	}

	static int suma(int a, int b){
		return a + b;
	}

	static void Main()
	{
		int x = 3;
		int y = 6;
		int r; // Es importante NO inicializar

		suma(x, y, out r);
		Console.WriteLine(r);

		Console.WriteLine(suma(x,y)); 

	}
}

```
Utilizando el modificador de parámetro **out**, especificamos que vamos a recibir
**por referencia** una variable **no** inicializada la cual inicializaremos dentro
del método.  

La mayoría de los casos es preferible que un método regrese un resultado en lugar de
recibir un argumento en el cual se guarde el resultado. La ventaja que tiene el guardar 
en un parámetro tipo **out** es que podríamos regresar varios al mismo tiempo. Antes de
utilizar este estilo, es recomendable que analices si no es mejor regresar varios valores
utilizando una estructura, un arreglo o lista.


## in

El modificador **in** es equivalente a un **ref** que nos garantiza que no habrá una modificación 
al parámetro que se pasa **por referencia**. Por ejemplo, en el caso anterior si en lugar de utilizar **ref**
utilizamnos **in**, no podríamos hacer la modificación. Al igual que con **ref** debemos pasar como argumento
una variable inicializada.

```csharp
using System;

class Duplicador{

	public void duplica(in int n) { 
			n = n*2;
	}


}

class Program
{
	static void Main()
	{
		Duplicador d = new Duplicador();
		int x = 2;
		d.duplica( in x); //Error, se intenta modificar el argumento
		Console.WriteLine(x);
	}
}

```
[Documentación](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters)




