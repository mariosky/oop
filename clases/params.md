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
variable de tipo valor **x**, inicializada en 2. La clase **Duplicador** podría estar implementada de 
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

En el caso de pase *por valor*, se hace una copia del valor que 
se está pasando (*x*) y 
se guarda localmente en *n*. El hacer una copia tiene un costo adicional 
pero en caso de que se modifique *n*, (como es el caso) este cambio
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
Vamos a cambiar la implementación del método **incrementa(int n)** en el código anterior para ver 
que sucede al pasar un parámetro tipo valor con la palabra **ref**. Es solo cuestión de agregar **ref**
al especificar el parámetro:

```csharp
	public void duplica( ref int n) { 
			n*=2;
	}
```

## out

## in




[Documentación](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters)




