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
literal o utulizando una variable.

Por ejemplo:

```csharp

Contador c = new Contador();

c.incrementa(1);
int x = 2;

c.incrementa(x);

Contador c2 = new Contador();
c2.incrementa(c1);

```

En el código anterior estamos llamando al método *incrementa()* del
objeto *c*, pasándole primero un entero literal *1*, después una
variable tipo valor *x* y finalmente le enviamos una variable
tipo referencia *c2* la cual se liga a otro contador. 

Decimos que el método *incrementa* tiene dos sobrecargas, una que
toma un entero (tipo valor) y otra que toma un objeto de la clase
Contador (tipo referencia).  Algo así (fragmento) :

```csharp
class Contador {
	
	public void incrementa(int n) { 

	}

	public void incrementa(Contador c) { 

	}

}

```

Por defecto, el paso de variables se hace *por valor*, 
vemos el siguente ejemplo:

```csharp

	public void incrementa(int n) { 

	}
```

En el caso de pase *por valor*, se hace una copia del valor que 
se está pasando (por ejemplo, *x*) y 
se guarda localmente en *n*. El hacer una copia tiene un costo, 
pero se tiene la ventaja de que se puede almacenar de manera más eficiente
y en caso de que se modifique *n*, (por ej. con un *n++*) este cambio
solo sucedera en la variable local y no en la original.

Ahora, esto es distinto para el caso de que pasemos variables tipo referencia

```csharp

	public void incrementa(Contador c) { 

	}
```

Ahora *c* recibe una referencia al objeto que se envía como 
parámetro, en este caso *c2*. Esto significa para empezar, que aunque también
se copia el valor, esta copia es una referencia al objeto original. Lo
que significa que *si* podríamos modificar al objeto *c2*, ya que
tenemos su referencia. ¡Esto puede ser muy peligroso! y como la mayoría 
de las cosas peligrosas, puede ser benéfica en ciertos casos. 

Con las siguientes palabras clave podemos especificar que el paso de
parámetros tenga un comportamiento distinto:

* *ref* con esta palabra especificamos que el paso de parámetros se hará por referencia incluso cuando las
variables sean de tipo valor. Nos permite modificar el valor del parámetro.

* *in* con esta palabra especificamos que el paso de parámetros se hará por referencia pero evitando que se modifique el parámetro original.

* *out* El objetivo es inicializar el valor de los parámetros y también se pasan por referencia.


## ref 

## out

## in




[Documentación](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters)




