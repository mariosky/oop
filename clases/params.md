# Paso de parámetros

Este tema no es característico de la  programación
orientada a objetos ya que se trata de técnicas de ejecución 
interna y no es exclusiva del paradigma. Sin embargo, conocer
del tema nos permitira hacer más eficientes algunas operaciones 
internas de nuestros programas. También nos permite restringir
la manera en la que interactúan las variables locales 
y las referencias que reciben como parámetros. 


Para entender bien el concepto de paso de parámetros
es importante recordar la diferencia entre los tipos de
variables: [de valor](https://docs.microsoft.com/es-mx/dotnet/csharp/language-reference/keywords/value-types) y [de referencia](https://docs.microsoft.com/es-mx/dotnet/csharp/language-reference/keywords/reference-types).


Cuando ejecutamos un método que requiere parámetros
decimos que le enviamos o pasámos los parámetros que necesita.
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
tipo referencia *c2* la cual es también otro contador. 

Decimos que el método *incrementa* tiene dos sobrecargas, una que
toma un entero (valor) y otra que toma un objeto de la clase
Contador (referencia).  Algo así (fragmento) :


```csharp
class Contador {
	
	public void incrementa(int n) { 

	}

	public void incrementa(Contador c) { 

	}

}

```


Internamente, la manera en la que se pasa el parámetro va a depender 
del tipo de variable que está recibiendo. 

```csharp

	public void incrementa(int n) { 

	}
```

Aquí el pase se hace *por valor*, es decir
se hace una copia del valor que se está pasando (por ejemplo, *x*) y 
se guarda localmente en *n*. El hacer una copia tiene un costo, 
pero se tiene la ventaja de que se puede almacenar de manera más eficiente
y en caso de que se modifique *n*, (por ej. con un *n++*) este cambio
solo sucedera en la variable local.

Ahora, para el caso de:

```csharp

	public void incrementa(Contador c) { 

	}
```

Ahora *c* recibe una referencia al objeto que se envía como 
parámetro, en este caso *c2*. Esto significa para empezar, que **no** se
copian los valores, se copia una referencia al objeto original. Lo
anterior también significaría que podríamos modificar al objeto *c2*, ya que
tenemos su referencia. ¡Esto puede ser muy peligroso! y como la mayoría 
de las cosas peligrosas, puede ser benéficas en ciertos casos. A continuación
veremos como sacar provecho o protegernos de esto.







