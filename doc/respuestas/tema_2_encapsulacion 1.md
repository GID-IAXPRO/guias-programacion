<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Encapsulación". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 2. Encapsulación

## 1. En Programación Orientada a Objetos (POO), ¿Qué buscan la **encapsulación** y **la ocultación** de información? Enumera brevemente algunas ventajas de la ocultación de información.

La Programación Orientada a Objetos (POO) enfatiza la encapsulación y la ocultación de información para mejorar la modularidad y seguridad del código. La ocultación de información proporciona seguridad al proteger los detalles internos de un objeto, garantizando un uso controlado y seguro. Favorece la modularidad al permitir cambios internos en un objeto sin afectar otras partes del programa, siempre que la interfaz pública no cambie. Además, facilita la abstracción al ofrecer interfaces simplificadas para los programadores, mejorando así la legibilidad y comprensión del código. Esta práctica también facilita el mantenimiento al reducir la complejidad y riesgo de errores en el sistema. 


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.


La interfaz pública en la Programación Orientada a Objetos define qué métodos y atributos son accesibles desde fuera de un objeto o clase, permitiendo la interacción con otros objetos. La ocultación de información protege los detalles internos del objeto, solo permitiendo el acceso a través de la interfaz pública. Esta relación entre la interfaz pública y la ocultación de información brinda una capa de abstracción que separa la implementación interna del objeto de su uso externo, promoviendo la modularidad y seguridad en el diseño de sistemas orientados a objetos. La interfaz pública limita el acceso a los métodos y atributos designados como públicos, mientras los detalles internos se mantienen privados y protegidos.

## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?


Es importante ser conscientes y diseñar con cuidado la interfaz pública de una clase en POO, ya que define la interacción de otros objetos y el acceso a su funcionalidad. Razones cruciales para diseñar la interfaz pública son: usabilidad, flexibilidad, seguridad y mantenimiento. Cambiar la interfaz pública de una clase puede ser complicado y disruptivo, dependiendo de la complejidad del sistema y la cantidad de código que depende de ella. Por lo tanto, es crucial diseñarla cuidadosamente desde el principio para minimizar cambios significativos en el futuro y facilitar la integración en diferentes partes del sistema.

## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

Las invariantes de clase son condiciones que deben mantenerse en todas las instancias de una clase para garantizar un estado consistente. La ocultación de información en la Programación Orientada a Objetos restringe el acceso a los detalles internos de un objeto, permitiendo la interacción solo a través de una interfaz pública. Esto ayuda a controlar el acceso, validar las modificaciones realizadas, mantener la modularidad y garantizar la seguridad del sistema. Al limitar el acceso a través de una interfaz bien definida, se facilita la tarea de mantener y garantizar las invariantes de clase durante modificaciones en el código, evitando situaciones inconsistentes o errores en el funcionamiento del sistema.


## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

```java
public class Punto {  
    private double x;  
    private double y;  
    public Punto(double x, double y) {  
        this.x = x;  
        this.y = y;  
    }  
    public double getX() {  
        return x;  
    }  
     public double getY() {        
	     return y;  
    }  
    public double calcularDistanciaAOrigen() {        
	    return Math.sqrt(x * x + y * y);  
    }  
}
```
En la clase `Punto` tiene dos atributos `x` e `y` que son de tipo `double` y están definidos como `private`. Esto significa que estos atributos son accesibles solo dentro de la propia clase `Punto` y no desde fuera de ella. La interfaz pública de la clase `Punto` incluye los métodos `getX()`, `getY()` y `calcularDistanciaAOrigen()`, que permiten obtener las coordenadas `x` e `y` de un punto y calcular su distancia al origen. En Java, los modificadores de accedidos desde cualquier clase, mientras que los atributos `x` e `y`, marcados como `private`, solo pueden ser accedidos dentro de la clase `Punto`.


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

En Java, los modificadores `public` y `private` se aplican a los miembros de una clase, como variables y métodos. `public` hace que el miembro sea accesible desde cualquier clase, mientras que `private` restringe el acceso solo a la misma clase. Los miembros públicos forman la interfaz pública y se usan fuera de la clase, mientras que los privados ocultan los detalles de implementación y aseguran la encapsulación de datos. Estos modificadores controlan el acceso a los miembros de una clase, definiendo claramente qué partes son accesibles externamente y cuáles son internas y privadas. Son esenciales para la seguridad y la estructura de una clase en Java.


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

En Programación Orientada a Objetos (POO), en Java, además de los modificadores de visibilidad `public` y `private`, también se utilizan los modificadores `protected` y `default`. Los miembros marcados como `public` son accesibles desde cualquier clase, `private` solo desde la misma clase. Los miembros `protected` son accesibles en el mismo paquete y por subclases, mientras que el modificador `default` brinda visibilidad de paquete, solo accesible dentro del mismo paquete. Otros lenguajes orientados a objetos como C++, C#, y Python también tienen conceptos similares con variantes en la implementación de los modificadores de acceso. A pesar de las diferencias en las reglas de visibilidad entre los lenguajes, todos siguen principios similares a los de Java en cuanto a controlar la accesibilidad de los miembros de una clase.


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

La respuesta correcta es: a) Los miembros de instancia privados de un objeto no se pueden acceder desde otras clases.
Cuando declaramos un miembro de instancia como privado en una clase en la programación orientada a objetos, significa que ese miembro solo es accesible desde dentro de la misma clase. Ni otras clases ni otros objetos (incluso si son de la misma clase) pueden acceder directamente a esos miembros privados.
una clase `Punto` en Java con un miembro privado `x`:
```java
public class Punto { 
	private double x; 
	private double y; 
 // Constructor 
	 public Punto(double x, double y) {
		 this.x = x;
		 this.y = y;
	 } // Método para calcular la distancia a otro punto
	 public double calcularDistanciaAPunto(Punto otro) { 
		 double distancia = Math.sqrt(Math.pow(this.x - otro.x, 2) + Math.pow(this.y - otro.y, 2));
		 return distancia;
	 } 
}
```
Como `x` y `y` son miembros de instancia privados de la clase `Punto`. Solo los métodos dentro de la clase `Punto` pueden acceder directamente a estos miembros privados.
Y si intentamos acceder directamente al miembro `x` desde otra clase:
```java
public class OtraClase {
	 public static void main(String[] args) {
		 Punto punto1 = new Punto(3.0, 4.0);
 // Esto daría un error de compilación
 // System.out.println(punto1.x);
	 }
}
```
Obtendríamos un error de compilación porque `x` es privado y no se puede acceder directamente desde fuera de la clase `Punto`.
Sin embargo, dentro de la clase `Punto`, el método `calcularDistanciaAPunto()` puede acceder al miembro `x` y `y` de otro objeto de la misma clase, ya que los miembros privados son accesibles dentro de la misma clase.
## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

Los métodos getter y setter son utilizados en la POO para acceder y modificar los atributos de un objeto de forma controlada. Un getter se utiliza para obtener el valor de un atributo privado, con un nombre que comienza con `get`. Son públicos y solo permiten lectura. Un setter se usa para modificar el valor de un atributo privado, con un nombre que comienza con `set`. También son públicos, pero permiten escribir en el atributo. En resumen, los getters proporcionan acceso de solo lectura a los atributos, mientras que los setters permiten modificar el valor de los atributos.
Ejemplo de un getter en Java:
```java
public class Persona {
	private String nombre;
// Getter para el atributo 'nombre'
	public String getNombre() {
		return nombre; 
	}
}
```
Ejemplo de un setter en Java:
```java
public class Persona {
	private String nombre;
// Setter para el atributo 'nombre'
	public void setNombre(String nuevoNombre) {
		this.nombre = nuevoNombre;
	}
}
```

## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

La ocultación de información en la Programación Orientada a Objetos (POO) no se refiere a la seguridad contra hackeos, sino al control de acceso y la prevención de manipulaciones no autorizadas. Se logra declarando atributos y métodos como privados y proporcionando una interfaz pública para interactuar con un objeto. Esto permite limitar el acceso a los detalles internos, agrupar datos y métodos relacionados, y evitar modificaciones no autorizadas en el estado interno de un objeto. Sin embargo, estos aspectos no garantizan la seguridad contra ataques maliciosos. Para abordar preocupaciones más amplias, como la protección contra amenazas externas, los desarrolladores deben considerar prácticas adicionales como la validación de datos, la gestión segura de contraseñas y el manejo de permisos, dependiendo del tipo de aplicación y entorno. La seguridad en programación es un tema complejo con múltiples capas y enfoques.


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

En programación orientada a objetos (POO), la diferencia principal entre los miembros de instancia y los miembros de clase está en su asociación con las instancias de una clase. Los miembros de instancia son específicos de cada objeto, con una copia por instancia, y se accede a través de una instancia específica sin el modificador `static`. En contraste, los miembros de clase pertenecen a la clase en su totalidad, con una única copia compartida por todas las instancias, y se accede a través del nombre de la clase con el modificador `static`. La ocultación de información se aplica principalmente a los miembros de instancia para controlar su acceso y manipulación, aunque también puede extenderse a los miembros de clase mediante modificadores de acceso y prácticas de diseño adecuadas.


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

Tener constructores privados puede ser útil en situaciones donde se desea controlar la instanciación de una clase, como en el patrón Singleton o Factory. Al hacerlo, se evita la creación de instancias desde fuera de la clase. Razones para hacerlo incluyen garantizar una única instancia en Singleton, utilizar un método estático como fábrica en Factory, o prevenir la creación accidental de instancias en clases utilitarias con solo métodos estáticos.


## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

Los miembros de clase en Java se indican utilizando el modificador `static`. Estos miembros pertenecen a la clase en su conjunto en lugar de a instancias individuales. 
```java
public class Punto { 
	private double x; 
	private double y; 
// Miembros de clase para rastrear los valores máximos 
	private static double maxX = Double.MIN_VALUE; 
	private static double maxY = Double.MIN_VALUE; 
	public Punto(double x, double y) { 
		this.x = x; 
		this.y = y; 
// Actualizar los valores máximos si es necesario 
		actualizarValoresMaximos(); 
	} 
	public double getX() { 
		return x; 
	} 
	public double getY() { 
		return y; 
	} 
	public double calcularDistanciaAPunto(Punto otro) { 
		double diferenciaX = this.x - otro.x; 
		double diferenciaY = this.y - otro.y; 
		return Math.sqrt(diferenciaX * diferenciaX + diferenciaY * diferenciaY); 
	} // Método privado para actualizar los valores máximos 
	private void actualizarValoresMaximos() { 
		maxX = Math.max(maxX, this.x); 
		maxY = Math.max(maxY, this.y); 
	} // Métodos estáticos para obtener los valores máximos 
	public static double getMaxX() { 
		return maxX;
	} 
	public static double getMaxY() { 
		return maxY;
	}
}
```
Como se ve, `maxX` y `maxY` son miembros de clase (`static`) que mantienen un seguimiento de los valores máximos de x e y encontrados en todos los puntos creados hasta el momento. El método `actualizarValoresMaximos()` se llama en el constructor de la clase cada vez que se crea un nuevo punto para garantizar que los valores máximos se actualicen correctamente. Además, se proporcionan métodos estáticos `getMaxX()` y `getMaxY()` para acceder a estos valores máximos desde fuera de la instancia de la clase `Punto`.


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

Sí, utilizaré el modificador `static` para crear un método de fábrica dentro de la clase `Punto` que construya un punto a partir de dos coordenadas y las redondee al entero más cercano. 
```java
public class Punto { 
// Otros miembros de la clase...
// Método de fábrica para construir un Punto redondeando las coordenadas al entero más cercano
	public static Punto crearPuntoRedondeado(double x, double y) {
		int xRedondeado = (int) Math.round(x); 
		int yRedondeado = (int) Math.round!;
		return new Punto(xRedondeado, yRedondeado);
	}
}
```
En este método `crearPuntoRedondeado`, se utilizan las funciones `Math.round()` para redondear las coordenadas `x` e `y` al entero más cercano, y luego se crea un nuevo objeto `Punto` con las coordenadas redondeadas. Este método es estático, lo que significa que se puede invocar directamente en la clase `Punto` sin necesidad de crear una instancia de la misma.



## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

Para cambiar la implementación de la clase `Punto` utilizando un array interno de dos posiciones en lugar de dos variables `double`, mantendremos la interfaz pública de la clase sin modificar para que los usuarios externos no necesiten conocer los cambios internos. 
```java
public class Punto { 
	private int[] coordenadas; 
// Array interno de dos posiciones para las coordenadas 
	public Punto(double x, double y) { 
		this.coordenadas = new int[2]; 
		this.coordenadas[0] = (int) Math.round(x); 
// Redondea x al entero más cercano 
		this.coordenadas[1] = (int) Math.round!; 
// Redondea y al entero más cercano
	} // Getter para obtener la coordenada x 
	public double getX() { 
		return this.coordenadas[0];
	} // Getter para obtener la coordenada y 
	public double getY() { 
		return this.coordenadas[1];
	} // Método para calcular la distancia entre dos puntos 
	public double calcularDistanciaAPunto(Punto otro) { 
		double diferenciaX = this.getX() - otro.getX(); 
		double diferenciaY = this.getY() - otro.getY();
		return Math.sqrt(diferenciaX * diferenciaX + diferenciaY * diferenciaY); 
	} // Método de fábrica estático para crear un Punto redondeando las coordenadas 
	public static Punto crearPuntoRedondeado(double x, double y) { 
	return new Punto(x, y); 
	} 
}
```
En la implementación, la clase `Punto` utiliza un array interno `coordenadas` de dos posiciones para almacenar las coordenadas x e y como enteros redondeados al entero más cercano. Los getters `getX()` y `getY()` acceden a las posiciones correspondientes del array interno para devolver las coordenadas.
El método `crearPuntoRedondeado()` se mantiene para crear instancias de la clase `Punto` a partir de coordenadas redondeadas, pero ahora las coordenadas se almacenan internamente como enteros en lugar de como doubles.



## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

La Programación Orientada a Objetos (POO) sugiere declarar atributos como privados y usar getters y setters públicos para acceder y modificarlos. Esto sigue el principio de encapsulación, ocultando detalles internos y controlando el acceso y modificación de objetos. Las ventajas incluyen control de acceso, flexibilidad para cambios internos sin afectar código externo, mayor consistencia y mantenimiento del código. Aunque se pueden usar atributos públicos, la mayoría de las prácticas favorecen la encapsulación con getters y setters para crear clases más robustas y mantenibles. Esta práctica facilita un diseño más claro y modular, permitiendo cambios internos sin afectar la interfaz pública.


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

Una clase inmutable no permite que los objetos cambien una vez creados, lo que significa que los valores iniciales no se pueden alterar. Se deben crear nuevos objetos con valores actualizados en lugar de modificar los existentes. Los métodos modificadores, como los setters, son utilizados para cambiar el estado interno de un objeto, alterando los valores de los atributos o realizando otras acciones que afecten la representación interna. Las clases inmutables ofrecen ventajas como seguridad de la concurrencia, facilidad de razonamiento, protección contra modificaciones no deseadas y mayor seguridad al prevenir errores. Sin embargo, la inmutabilidad no siempre es la mejor opción, ya que puede resultar en mayor consumo de memoria o rendimiento inferior al tener que crear nuevos objetos en lugar de modificar los existentes. La elección entre una clase inmutable o mutable depende del contexto y los requisitos del diseño del sistema.


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

No siempre es aconsejable incluir setters para todos los atributos de una clase. La decisión depende del diseño y requisitos específicos de la clase y sistema. Los setters permiten modificar los atributos desde fuera, pero pueden comprometer la encapsulación y control de acceso. Seguir el principio de mínima exposición implica exponer solo lo necesario. En casos de inmutabilidad o diseño defensivo, es preferible evitar setters. Se pueden ofrecer métodos específicos en lugar de setters para operaciones más controladas. Es importante considerar el diseño y evolución futura al decidir incluir setters, ya que pueden hacer una clase más flexible pero también introducir complejidad y dificultar el mantenimiento.

## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

La clase `String` en Java es inmutable, por lo que cualquier operación que modifique una cadena en realidad crea una nueva cadena en lugar de modificar la original. Al concatenar cadenas con el operador `+` o `concat()`, se crea una nueva cadena sin modificar la original.
```java
String cadena1 = "Hola"; String cadena2 = " Mundo"; String resultado = cadena1 + cadena2; // Se crea una nueva cadena
```
Para operaciones que requieren construir cadenas largas de manera eficiente, se recomienda utilizar `StringBuilder`, que es mutable y permite modificaciones eficientes en el contenido de la cadena sin crear nuevas instancias en cada concatenación.
```java
StringBuilder resultadoBuilder = new StringBuilder(); resultadoBuilder.append("Hola"); resultadoBuilder.append(" Mundo"); String resultadoFinal = resultadoBuilder.toString(); // Se crea una cadena al final
```


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 


En la Programación Orientada a Objetos (POO), la comparación de objetos de una misma clase puede basarse en la identidad y el contenido. La comparación por identidad verifica si dos referencias apuntan al mismo objeto en memoria, utilizando el operador `==`. Por otro lado, la comparación por contenido evalúa si los valores internos de dos objetos son iguales, usando métodos como `equals()`. En Java, la clase `Object` tiene un método `equals()` que compara por identidad, pero se recomienda que las clases personalizadas lo sobrescriban para comparaciones por contenido. Para comparar contenido de cadenas en Java, se utiliza el método `equals()` de la clase `String`, que compara los caracteres y no la identidad de los objetos.


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

Las clases wrapper en programación orientada a objetos encapsulan tipos primitivos para que se comporten como objetos y proporcionan funcionalidades adicionales y métodos para manipularlos en dicho entorno. En Java, por ejemplo, existen clases wrapper como `Integer` para `int`, `Double` para `double`, `Boolean` para `boolean`, etc. 
Estas clases se pueden instanciar explícitamente con constructores o implícitamente mediante autoboxing, convirtiendo automáticamente un tipo primitivo en su clase wrapper correspondiente. 
```java 
int entero = 10; Integer objetoEntero = entero; // Autoboxing, convierte int a Integer automáticamente
```
Por otro lado, unboxing convierte un objeto wrapper en su tipo primitivo cuando es necesario. 
```java 
Integer objetoEntero = 20; int entero = objetoEntero; // Unboxing, convierte Integer a int automáticamente
```
Las ventajas de las clases wrapper incluyen la posibilidad de trabajar con tipos primitivos como objetos, compatibilidad con colecciones genéricas y algoritmos, y funcionalidades adicionales como conversiones y operaciones matemáticas. En lenguajes sin tipos primitivos como Python, las clases wrapper no son necesarias, pero en entornos orientados a objetos como Java, son esenciales para manejar tipos primitivos como objetos.
## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

En Programación Orientada a Objetos, un enum es una forma de representar un conjunto fijo de valores constantes relacionados. En Java, se declara con la palabra clave `enum` y se puede tener métodos y campos. 
```java 
public enum DiaSemana { LUNES, MARTES, MIERCOLES, JUEVES, VIERNES, SABADO, DOMINGO }
```
Los enums en Java ofrecen ventajas en encapsulación: 
1. Valores constantes y legibilidad mejorada, evitando valores mágicos.
2. Seguridad de tipo al limitar la variable a valores enumerados, previniendo asignaciones incorrectas.
3. Mantenimiento simple al modificar el enum para añadir o cambiar valores. 
4. Metadatos extra como campos y métodos para asociar información adicional a cada valor. 
Los enums facilitan el mantenimiento del código y mejoran la comprensión.

## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado.

```java
public enum Mes { 
	ENERO(31), 
	FEBRERO(28), 
	MARZO(31), 
	ABRIL(30), 
	MAYO(31), 
	JUNIO(30), 
	JULIO(31), 
	AGOSTO(31), 
	SEPTIEMBRE(30), 
	OCTUBRE(31), 
	NOVIEMBRE(30), 
	DICIEMBRE(31); 
	private final int dias; 
	Mes(int dias) { 
		this.dias = dias; 
	} 
	public int getDias(){ 
		return dias; 
	} 
}
```
En este código, cada constante de la enumeración `Mes` tiene asociada la cantidad de días que tiene ese mes. Se define un atributo `dias` privado y se proporciona un constructor que recibe el número de días como parámetro para cada instancia de `Mes`. Luego, se provee un método `getDias()` para obtener la cantidad de días de cada mes.
Puedes usar este enum `Mes` de la siguiente manera:
```java
public class Main {
	public static void mian (string[] args){
		Mes mesActual = Mes.Febrero;
		System.out.println("Dias en " + mesActual + ": " mesActual.getDias());
		}
}
```
## 24. Añade a la clase `Mes` del ejercicio anterior cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

```java 
public class Mes {
    private int numero; // Del 1 al 12
    public Mes(int numero) {
        this.numero = numero;
    }
    // --- Métodos de Estaciones ---
    public boolean esDeInvierno(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            // Norte: Diciembre, Enero, Febrero, Marzo
            return (numero == 12 || numero == 1 || numero == 2 || numero == 3);
        } else {
            // Sur: Junio, Julio, Agosto, Septiembre
            return (numero == 6 || numero == 7 || numero == 8 || numero == 9);
        }
    }
    public boolean esDePrimavera(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            // Norte: Marzo, Abril, Mayo, Junio
            return (numero == 3 || numero == 4 || numero == 5 || numero == 6);
        } else {
            // Sur: Septiembre, Octubre, Noviembre, Diciembre
            return (numero == 9 || numero == 10 || numero == 11 || numero == 12);
        }
    }
    public boolean esDeVerano(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            // Norte: Junio, Julio, Agosto, Septiembre
            return (numero == 6 || numero == 7 || numero == 8 || numero == 9);
        } else {
            // Sur: Diciembre, Enero, Febrero, Marzo
            return (numero == 12 || numero == 1 || numero == 2 || numero == 3);
        }
    }
    public boolean esDeOtoño(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            // Norte: Septiembre, Octubre, Noviembre, Diciembre
            return (numero == 9 || numero == 10 || numero == 11 || numero == 12);
        } else {
            // Sur: Marzo, Abril, Mayo, Junio
            return (numero == 3 || numero == 4 || numero == 5 || numero == 6);
        }
    }
}
```
