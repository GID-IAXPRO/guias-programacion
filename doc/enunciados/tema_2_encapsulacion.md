1. En Programación Orientada a Objetos (POO), ¿Qué buscan la encapsulación y la ocultación de información? Enumera brevemente algunas ventajas de la ocultación de información.

La ***encapsulación*** y la ***ocultación de información*** buscan proteger el estado interno de un objeto y controlar cómo se accede y modifica, de modo que el uso del objeto sea seguro, coherente y predecible.

De este modo evito estados no válidos de mis objetos y oculten los datos que no deben ser modificados desde fuera.

Agrupa *datos* (atributos) y *comportamientos* (métodos) dentro de una misma entidad (la clase). Su objetivo es que el objeto gestione su propio estado.

1. ¿Qué se entiende por la interfaz pública de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

La ***interfaz pública*** de un objeto o clase es el conjunto de métodos y atributos accesibles desde fuera de esa clase. Es la *“cara visible” del objeto*. (Define qué puede hacerse con objetos.)

- Métodos públicos que permiten realizar operaciones (por ejemplo, `depositar()`, `calcularTotal()`, `mover()`).
- Atributos públicos (aunque en buena práctica suelen evitarse).
- Constantes o tipos públicos definidos dentro de la clase.

<aside>
💡

La interfaz pública exite porque la ocultación de información obliga a que cualquier interacción con el estado interno pase por ella, separando 2 niveles:

- *Lo interno (privado/protegido)*: datos y lógica que la clase mantiene en secreto para proteger su estado.
- *Lo externo (público)*: los puntos de acceso controlados que permiten usar el objeto sin romper su coherencia.
</aside>

1. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la interfaz pública de una clase? ¿Es fácil cambiarla?

La interfaz pública de una clase debe diseñarse con cuidado porque actúa como el *contrato estable* mediante el cual el resto del sistema interactúa con ella. Cambiarla después suele ser costoso y arriesgado, ya que cualquier modificación puede romper código que depende de esa interfaz.

1. ¿Qué son las invariantes de clase y por qué la ocultación de información nos ayuda?

Las ***invariantes de clase*** son las condiciones que siempre deben cumplirse para que un objeto sea válido durante toda su vida útil. Son permanentes y se cumplen después de construir el objeto y después de cada operación pública.

Ejemplos:

- En una clase CuentaBancaria el saldo debe ser +
- Una contraseña debe tener como mínimo 3 caracteres
- En Persona la edad debe ser ≥ 0

1. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

```jsx
class Punto {
// Atributos privados (ocultación de info)
	private double x;
	private double y;
	
	// Constructor
	public Punto (double x, double y) {
		this.x = x;
		this.y = y;
	}
	
	// Métodos públicos de acceso (getters)
    public double getX() {
        return x;
    }
    public double getY() {
        return y;
    }
	
	// Método público para calcular distancia
	public double distanciaAOrigen () {
		return Math.sqrt(this.x + this.x + this.y + this.y);
	}
}
```

- ***public*** — El elemento es accesible desde cualquier parte del programa. Forma parte de la interfaz pública de la clase:
    - Punto(double x, double y)
    - double getX()
    - double getY()
    - double calcularDistanciaAOrigen()
- ***private*** — El elemento solo es accesible desde dentro de la propia clase. Queda oculto al exterior, protegiendo el estado interno.

<aside>
💡

Se pone "this." para referirnos al campo de instancia de la clase actual y evitar ambigüedades

</aside>

1. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

En java

- ***Clases (de nivel superior)***
    
    `public` — La clase es accesible desde cualquier paquete.
    
    (sin modificador, “package‑private”) — Solo accesible dentro del mismo paquete.
    
    `private` — No permitido en clases de nivel superior.
    
- ***Clases internas (dentro de otra clase)***
    
    Pueden ser `public`, `private`, `protected` o `package-private`.
    
    Esto permite encapsular clases auxiliares que no deben usarse desde fuera.
    
- ***Atributos (variables de instancia o estáticas)***
    
    Pueden ser `public`, `private`, `protected` o `package-private`.
    
    En buena práctica, casi siempre private para proteger el estado interno.
    
- ***Métodos***
    
    Pueden ser `public`, `private`, `protected` o `package-private`.
    
    Los métodos públicos forman la interfaz pública de la clase.
    
- ***Constructores***
    
    También pueden ser `public`, `private`, `protected` o `package-private`.
    
    Un constructor private se usa, por ejemplo, en patrones como Singleton o Factory Method.
    

7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

Niveles de visibilidad en *Java*:

- `public` — Accesible desde cualquier parte del programa, incluso desde otros paquetes.
- `private` — Accesible solo dentro de la propia clase.
- `protected` — Accesible dentro de la clase, dentro del paquete y por clases hijas (incluso si están en otro paquete).
- `package-private` — Accesible solo dentro del mismo paquete.
- 

*C++*: `public` , `private`  y `protected`

*Python* (usa convenciones):

- `_atributo` → “protegido” por convención.
- `__atributo` → name mangling, que dificulta el acceso externo.

1. Responde: Los miembros de instancia privados de un objeto están ocultos para

a) otras clases

b) otras instancias, aunque sean de la misma clase.

Pon un ejemplo añadiendo un método calcularDistanciaAPunto(Punto otro) y explica la respuesta.

```jsx
public class Punto {

    private double x;
    private double y;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x;   // Acceso permitido: estamos dentro de la misma clase
        double dy = this.y - otro.y;
        return Math.sqrt(dx * dx + dy * dy);
    }
}
```

- `otro.x` y `otro.y` son privados, pero el acceso ocurre dentro de la clase Punto.
- Java interpreta `private` como “solo accesible desde el código de esta clase”, no como “solo accesible desde este objeto concreto”

9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

Son operaciones públicas que permiten *leer* (***getter***) y *modificar* (***setter***) atributos privados de un objeto respetando la encapsulación.

1.  Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

No. Esto no tiene que ver con la ciberseguridad, es facilitar una programación con menos bugs.

1. ¿Qué diferencia hay entre miembro de instancia y miembro de clase? ¿Los miembros de clase también se pueden ocultar?

***Miembro de clase***: pertenece a la clase en sí misma, compartido por *todas* las instancias

Son los atributos y métodos marcados como static.
Existe una única copia para toda la clase, compartida por todas las instancias.

- Ejemplo: `private static int contadorDePuntos;`
- Todas las instancias ven y modifican el mismo contador.

***Miembro de instancia***: pertenece a cada objeto individual, mientras que un miembro de clase 

Son los atributos y métodos no estáticos.
Cada objeto tiene su propia copia.

- Ejemplo: `private double x;` en la clase `Punto`.
- Cada `new Punto(...)` tiene su propio `x`.

1. Brevemente: ¿Tiene sentido que los constructores sean privados?

Sí tiene sentido en situaciones concretas. Un ***constructor privado*** impide crear objetos desde fuera de la propia clase, y eso permite controlar estrictamente *cuándo* y *cómo* se crean las instancias.

- La clase no puede ser instanciada desde fuera.
- La propia clase debe proporcionar alguna forma alternativa de obtener instancias (si es que deben existir).
- Se refuerza la encapsulación porque se controla completamente el ciclo de vida del objeto.

```jsx
public class Configuracion {

    private static final Configuracion instancia = new Configuracion();

    private Configuracion() {
        // Constructor privado
    }

    public static Configuracion getInstancia() {
        return instancia;
    }
}
```

1. ¿Cómo se indican los miembros de clase en Java? Pon un ejemplo, en la clase Punto definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores x e y máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

Con `static`

```jsx
public class Punto {

    // Miembros de instancia
    private double x;
    private double y;

    // Miembros de clase (compartidos por todos los objetos)
    private static double maxX = Double.NEGATIVE_INFINITY;
    private static double maxY = Double.NEGATIVE_INFINITY;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;

        // Actualizar máximos globales
        if (x > maxX) {
            maxX = x;
        }
        if (y > maxY) {
            maxY = y;
        }
    }

    // Getters de instancia
    public double getX() { return x; }
    public double getY() { return y; }

    // Getters de clase
    public static double getMaxX() { return maxX; }
    public static double getMaxY() { return maxY; }
}
```

1. Como sería un método factoría dentro de la clase Punto para construir un Punto a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado static?

Debe ser un método *estático* (`static`) porque crea objetos sin necesitar una instancia previa. 

```jsx
public static Punto crearRedondeado(double x, double y) {
    return new Punto(Math.round(x), Math.round(y));
}
```

1.  Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

Modificar los atributos privados y los métodos internos, *sin alterar la interfaz pública* (constructores, getters, métodos públicos…).

```jsx
public class Punto {

    // Representación interna cambiada: ahora un array
    private double[] coords = new double[2];

    public Punto(double x, double y) {
        coords[0] = x;
        coords[1] = y;
    }

    public double getX() {
        return coords[0];
    }

    public double getY() {
        return coords[1];
    }

    public double calcularDistanciaAOrigen() {
        return Math.sqrt(coords[0] * coords[0] + coords[1] * coords[1]);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.coords[0] - otro.coords[0];
        double dy = this.coords[1] - otro.coords[1];
        return Math.sqrt(dx * dx + dy * dy);
    }

    // Método factoría pedido anteriormente
    public static Punto crearRedondeado(double x, double y) {
        return new Punto(Math.round(x), Math.round(y));
    }
}
```

1. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

Un atributo público expone directamente el estado interno del objeto. Eso implica:

- No puedes validar valores antes de asignarlos.
- No puedes impedir estados incoherentes.
- No puedes cambiar la representación interna sin romper código externo.
- Cualquier parte del programa puede modificar el atributo sin control.

Un *setter*, en cambio, permite introducir reglas, validaciones o restricciones. Un *getter* permite devolver copias defensivas si el atributo es mutable. Y ambos permiten cambiar la implementación interna sin afectar a quien usa la clase.

La ***convención habitual*** es hacer el *método privado*.

1. ¿Qué significa que una clase sea inmutable? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

Que una clase sea ***inmutable*** significa que sus objetos no pueden cambiar de estado después de ser creados.

Un método modificador es cualquier método que cambia el estado interno del objeto. Puede hacerlo directamente o a través de setters, pero lo esencial es que altera atributos.

Ejemplos típicos:

```
setX(…)
mover(dx, dy) que cambia las coordenadas
depositar(cantidad) en una cuenta bancaria
```

*VENTAJAS:*

- Seguridad frente a errores: el estado no cambia inesperadamente.
- Hilos y concurrencia más simples: no requieren sincronización porque no hay cambios de estado.
- Mayor facilidad para razonar sobre el código: cada objeto es un valor fijo.
- Mejor encapsulación: no hay riesgo de romper invariantes internas.
- Uso seguro como claves en estructuras de datos (por ejemplo, en HashMap).
- Mayor robustez: si se pasa un objeto a otro método, no puede ser modificado desde fuera.

1. ¿Es recomendable incluir métodos "setter" siempre y como convención?

No es recomendable incluir setters siempre por defecto. Un setter permite modificar un atributo en cualquier momento, desde cualquier parte del programa que tenga acceso al objeto.

Eso puede debilitar la encapsulación, dificultar mantener las invariantes de clase (porque cualquier código externo puede dejar el objeto en un estado inválido), aumentar el acoplamiento e impedir que la clase controle su propia coherencia.

Lo habitual en Java, C++ y otros lenguajes orientados a objetos es poner atributos privados, getters solo cuando son necesarios y setters solo cuando la clase necesita permitir cambios controlados

1. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

La clase String es *inmutable***.** Por esta razón cada concatenación genera un nuevo objeto String.

En la práctica se recomienda usar:

- `StringBuilder`: no sincronizado, más rápido
- `StringBuffer` : sincronizado, seguro en entornos multihilo

1. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java?

En POO, dos objetos pueden compararse por:

- ***Identidad***: dos referencias apuntan al *mismo* objeto en memoria (==)
- ***Contenido**:* dos objetos *distintos* tienen los *mismos valores internos* ( `.equals()` )

La implementación por defecto de `equals`  compara por *identidad (*equilavente a ==), excepto en clases concretas donde se realiza una comparación por *contenido* (ej: String)

2 cadenas deben compararse utilizando `equals` 

```jsx
 String s1 = new String("Hola");
 String s2 = new String("Hola");
 
// Por identidad
 if (s1==s2){
	 return true;
 } // Devuleve falso, porque no es la misma dirección de memoria
	
// Por contenido
 if (s1.equals(s2)) {
	 return true;
 } // Devuelve verdadero, porque es el mismo contenido
```

1. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers?

Las clases ***wrapper*** son clases que contienen un tipo primitivo para tratarlo como un objeto y y ofrece métodos para manipularlo, convertirlo o representarlo. Esto es algo necesario en lenguajes orientados a objetos que distinguen entre tipos primitivos y tipos de referencia. Ejemplos: java (con tipos primitivos), python (sin tipos primitivos).

*Wrappers en Java:*

- `int` → `Integer`
- `double` → `Double`
- `boolean` → `Boolean`
- `char` → `Character`
- `long` → `Long`
- `float` → `Float`
- `byte` → `Byte`
- `short` → `Short`

En java convertir un primitivo en su wrapper se llama *autoboxing*, y convertir su wrapper en primitivo es *unboxing.*

```jsx
Integer x = 5;      // autoboxing: int → Integer
int y = x;          // unboxing: Integer → int
```

*VENTAJAS:*

- Usar valores primitivos en *colecciones* (`ArrayList<Integer>`, no `ArrayList<int>`).
- Representar la *ausencia de valor* con `null` (algo que un primitivo no puede hacer).
- *Acceder a métodos* útiles (por ejemplo, `Integer.parseInt`, `Double.isNaN`).
- Trabajar con *genéricos*, que solo aceptan objetos.
- Integrarse con APIs que requieren tipos de referencia.

1. ¿En POO qué es un tipo de dato enumerado? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

Un enumerado es un tipo con un número determinado de valores posibles. Cada valor del `enum` es una *instancia única* (singleton) de esa clase.

En java es una clase cuyas instancias son finitas y son conocidas de antemano.

- *Espacio de valores cerrado*: Solo existen los valores definidos en el `enum` (No se pueden crear otros desde fuera porque el constructor es privado).
- *Evitan valores inválidos*: En lugar de usar enteros o cadenas (propensos a errores), un enum garantiza que solo se usen valores válidos.
- *Encapsulan comportamiento*: Un enum puede tener métodos, atributos, constructores privados y comportamiento distinto por constante. Esto permite que el tipo sea autosuficiente y mantenga su propia lógica interna.
- *Comparación segura:* Los enums se comparan por identidad (==), porque cada valor es único. Esto evita errores típicos de comparar cadenas o números.
- *Integración con switch y colecciones:* Son más eficientes y expresivos que usar constantes numéricas o cadenas.

1. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado.

```jsx
public enum Mes {

    ENERO(1, 31),
    FEBRERO(2, 28),   // Sin contemplar años bisiestos aquí
    MARZO(3, 31),
    ABRIL(4, 30),
    MAYO(5, 31),
    JUNIO(6, 30),
    JULIO(7, 31),
    AGOSTO(8, 31),
    SEPTIEMBRE(9, 30),
    OCTUBRE(10, 31),
    NOVIEMBRE(11, 30),
    DICIEMBRE(12, 31);

    private final int ordinalMes;
    private final int dias;

    Mes(int ordinalMes, int dias) {
        this.ordinalMes = ordinalMes;
        this.dias = dias;
    }

    public int getOrdinalMes() {
        return ordinalMes;
    }

    public int getDias() {
        return dias;
    }
}
```

1. Añade a la clase `Mes` del ejercicio anterior cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

```jsx
public enum Mes {

    ENERO(1, 31),
    FEBRERO(2, 28),
    MARZO(3, 31),
    ABRIL(4, 30),
    MAYO(5, 31),
    JUNIO(6, 30),
    JULIO(7, 31),
    AGOSTO(8, 31),
    SEPTIEMBRE(9, 30),
    OCTUBRE(10, 31),
    NOVIEMBRE(11, 30),
    DICIEMBRE(12, 31);

    private final int ordinalMes;
    private final int dias;

    Mes(int ordinalMes, int dias) {
        this.ordinalMes = ordinalMes;
        this.dias = dias;
    }

    public int getOrdinalMes() {
        return ordinalMes;
    }

    public int getDias() {
        return dias;
    }

    public boolean esDeInvierno(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            return this == DICIEMBRE || this == ENERO || this == FEBRERO;
        } else {
            return this == JUNIO || this == JULIO || this == AGOSTO;
        }
    }

    public boolean esDePrimavera(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            return this == MARZO || this == ABRIL || this == MAYO;
        } else {
            return this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE;
        }
    }

    public boolean esDeVerano(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            return this == JUNIO || this == JULIO || this == AGOSTO;
        } else {
            return this == DICIEMBRE || this == ENERO || this == FEBRERO;
        }
    }

    public boolean esDeOtono(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            return this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE;
        } else {
            return this == MARZO || this == ABRIL || this == MAYO;
        }
    }
}
```

## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado.

### Respuesta


## 24. Añade a la clase `Mes` del ejercicio anterior cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### Respuesta
