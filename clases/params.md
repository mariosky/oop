# Paso de parámetros

El paso de parámetros no es un tema exclusivo de la  programación
orientada a objetos, ya que la mayoría de los lenguajes de programación
permiten la definición de [funciones que aceptan parámetros](https://es.wikipedia.org/wiki/Argumento_(inform%C3%A1tica)).
Independientemente del lenguaje que estemos utilizando, es importante 
conocer como se realiza internamente el paso de parámetros, ya que esto
nos permitira hacer más eficientes nuestros programas.

Para entender bien los conceptos de paso de parámetros en C#,
es importante recordar la diferencia entre los tipos de
variables: [de valor](https://docs.microsoft.com/es-mx/dotnet/csharp/language-reference/keywords/value-types) y [de referencia](https://docs.microsoft.com/es-mx/dotnet/csharp/language-reference/keywords/reference-types).


Cuando ejecutamos un método que requiere parámetros
decimos que le enviamos o pasámos los parámetros que necesita, ya sea de manera
literal o utilizando una variable.

Por ejemplo, analizemos este fragmento de código:

```csharp

Duplicador d = new Duplicador();

d.duplica(1);

int x = 2;

d.duplica(x);

```

En el código anterior estamos llamando dos veces al método **duplica(int x)** del
objeto **d**, pasándole como parámetro un entero literal **1**, después una
variable de tipo valor **x**, inicializada en **2**. La clase **Duplicador** podría estar implementada de 
la siguiente manera: 

```csharp
class Duplicador{

	public void duplica(int n) { 
			n = n*2;
	}

}
```

Por defecto en C# el paso de variables se hace **por valor**, 
veamos el concepto en el ejemplo y preguntándonos ¿Qué valor 
tiene **x** al imprimirse?:

```csharp
Duplicador d = new Duplicador();
int x = 2;
d.duplica(x);
Console.WriteLine(x);
```

En el caso de pase **por valor**, se hace una copia del valor que 
se está pasando (**x**) y 
se guarda localmente en **n**. El hacer una copia tiene un costo adicional 
pero en caso de que se modifique **n**, (como es el caso) este cambio
solo sucederá en la variable local y no en la original. Por lo que sabemos
que se imprimiría **2**. 

Ahora, esto es distinto para el caso de que pasemos variables tipo referencia,
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
parámetro, en este caso **espía** y se copia a **p**. Esto significa para empezar, que aunque también
se copia el valor, esta copia es una **referencia** al objeto original. El contar con una referencia 
significa que a diferencia de una variable tipo valor como en el ejemplo anterior,
ahora **si** podríamos modificar al objeto que recibimos, ya que
tenemos su referencia. ¡Esto puede ser muy peligroso! aunque como la mayoría 
de las cosas peligrosas, puede ser benéfica en ciertos casos. 
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





## out

## in




[Documentación](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters)




