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

### Respuesta

La encapsulación s busca agrupar dentro de una misma clase tanto los datos como las operaciones que actúan sobre ellos, evitando que otras partes del programa accedan o modifiquen directamente.

La ocultación de información pretende controlar qué detalles internos de una clase quedan visibles desde el exterior y cuáles permanecen privados

La ocultación de información evita dependencias innecesarias entre módulos, también reduce la probabilidad de errores al impedir modificaciones accidentales, favorece la reutilización de componentes, ya que otros desarrolladores pueden utilizarlos sin necesidad de conocer detalles internos y permite asegurar la coherencia del estado de los objetos mediante métodos que controlan los cambios en sus atributos.


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### Respuesta
La interfaz pública de una clase u objeto se entiende como el conjunto de métodos y atributos accesibles desde fuera de la propia clase sin necesidad de exponer cómo están implementadas internamente. 

La ocultación de información permite separar qué se muestra y qué se mantiene oculto. Los detalles internos —atributos privados, estructuras auxiliares, algoritmos— quedan protegidos mediante modificadores como private o protected,

## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### Respuesta
La interfaz pública de una clase debe diseñarse con cuidado porque actúa como el contrato que otros componentes del programa utilizarán para interactuar con ella
Si se diseña sin reflexión, pueden exponerse métodos innecesarios o permitir usos incorrectos del objeto.

Cambiar la interfaz pública no es sencillo, porque cualquier modificación impacta directamente en todo el código que la utiliza. Es recomendable exponer solo lo esencial y mantener la interfaz estable


## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Respuesta

Las invariantes de clase son condiciones que deben cumplirse siempre para que un objeto sea considerado válido durante toda su vida, excepto en momentos puntuales dentro de la ejecución.
Por ejemplo, en una cuenta bancaria, una invariante típica sería que el saldo nunca sea negativo si la clase no permite descubiertos.

La ocultación de información ayuda porque impide el acceso directo e indiscriminado a los atributos internos, lo que evita que código externo rompa accidentalmente estas invariantes


## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### Respuesta
    public class Punto {
    // Atributos ocultos
    private double x;
    private double y;

    // Constructor
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Métodos de acceso (interfaz pública)
    public double getX() {
        return x;
    }

    public double getY() {
        return y;
    }

    // Método de cálculo (interfaz pública)
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
    }

La interfaz pública de la clase Punto está formada por los elementos que cualquier otro código puede invocar desde fuera de la clase. 
En cambio, private restringe el acceso únicamente al interior de la propia clase.


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### Respuesta

En primer lugar, ambos modificadores pueden aplicarse a los atributos y métodos de una clase.

Además, public puede aplicarse a las clases de primer nivel.Sin embargo, private no puede utilizarse en estas; solo es válido para clases internas (clases definidas dentro de otra clase).

Por último, los modificadores también se pueden usar en constructores 


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### Respuesta
En Java existen cuatro niveles de visibilidad: public, private, protected y la visibilidad por defecto (o package‑private).
"protected" permite el acceso desde la propia clase, su paquete y sus subclase.
"package‑private" permite acceso solo dentro del mismo paquete

En otros lenguajes también existen más niveles
En C#, además, existen modificadores como internal (similar al package‑private de Java pero basado en ensamblados) y protected internal.
Otros lenguajes, como Python, no implementan visibilidad estricta a nivel del lenguaje, usan convenciones como _atributo o __atributo para indicar intención de ocultación


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### Respuesta
Los miembros de instancia declarados como private están ocultos solo para otras clases, pero no están ocultos para otras instancias de la misma clase

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

    // Acceso a atributos privados de otra instancia de la misma clase
    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x;  // Acceso permitido
        double dy = this.y - otro.y;  // Acceso permitido
        return Math.sqrt(dx * dx + dy * dy);
    }
}

Este comportamiento permite implementar métodos como calcularDistanciaAPunto(Punto otro), que necesitan leer las coordenadas privadas de otro objeto Punto. Aunque las coordenadas del parámetro otro sean privadas, el método puede acceder a ellas sin problema porque se encuentra dentro del cuerpo de la misma clase


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Respuesta
Los métodos getter y setter son funciones utilizadas en lenguajes orientados a objetos para acceder y modificar de forma controlada los atributos privados de una clase.

Un getter permite obtener el valor de un atributo sin exponerlo directamente, mientras que un setter permite asignarle un nuevo valor aplicando, si es necesario, validaciones o restricciones.

Estos métodos forman parte de la interfaz pública de la clase y actúan como intermediarios entre el exterior y los datos encapsulados


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### Respuesta

En este contexto, “seguridad” se entiende como seguridad lógica o interna del diseño del programa, es decir, la capacidad de mantener un estado interno coherente y evitar errores provocados por accesos o modificaciones inadecuadas

## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### Respuesta
Un miembro de instancia es aquel que pertenece a cada objeto individual. Los métodos de instancia también operan sobre una instancia concreta, y suelen utilizar el estado particular del objeto a través de this

Por el contrario, un miembro de clase es compartido por todas las instancias, ya que pertenece a la clase en sí. Esto implica que existe una única copia del atributo o método para toda la clase. En Java, estos miembros se declaran con static. 

Tanto los miembros de instancia como los miembros de clase pueden ocultarse utilizando modificadores como private


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Respuesta
Aunque lo habitual es que un constructor sea público para permitir crear objetos libremente; declararlo como private permite controlar completamente cómo y cuándo se crean las instancias de una clase

Un uso típico es el patrón Singleton, donde se garantiza que solo exista una única instancia de la clase. Otro caso común aparece cuando se emplean métodos de fábrica (factory methods) que devuelven objetos ya configurados y que ocultan los detalles de creación al exterior.


## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### Respuesta
los miembros de clase se indican utilizando la palabra clave static. Esto hace que dichos miembros pertenezcan a la clase en sí y no a cada instancia individual

public class Punto {
    // Miembros de instancia
    private double x;
    private double y;

    // Miembros de clase (compartidos por todos los objetos)
    private static double maxX = Double.NEGATIVE_INFINITY;
    private static double maxY = Double.NEGATIVE_INFINITY;

    // Constructor
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;

        // Actualización de los máximos
        if (x > maxX) maxX = x;
        if (y > maxY) maxY = y;
    }

    // Getters de instancia
    public double getX() { return x; }
    public double getY() { return y; }

    // Getters de clase (interfaz pública para acceder a los máximos)
    public static double getMaxX() { return maxX; }
    public static double getMaxY() { return maxY; }
}


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

### Respuesta
public static Punto crearRedondeado(double x, double y) {
    long rx = Math.round(x);
    long ry = Math.round(y);
    return new Punto(rx, ry);
}


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### Respuesta

public class Punto {

    // Array interno en lugar de dos double
    private double[] coords = new double[2];

    public Punto(double x, double y) {
        this.coords[0] = x;
        this.coords[1] = y;
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

    // Ejemplo: método factoría del ejercicio anterior
    public static Punto crearRedondeado(double x, double y) {
        long rx = Math.round(x);
        long ry = Math.round(y);
        return new Punto(rx, ry);
    }
}


## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### Respuesta
Un atributo público puede cambiarse libremente desde cualquier parte del programa. En cambio, un setter permite validar, transformar o restringir el dato antes de asignarlo, y un getter puede calcular valores derivados, aplicar formatos o simplemente preservar la consistencia de la interfaz pública.

Lo habitual es que los atributos sean privados y la clase exponga solo los métodos necesarios para manipularlos.
Esta decisión está directamente relacionada con las invariantes de clase, es decir, aquellas condiciones que deben cumplirse siempre para que un objeto sea válido. Si los atributos fueran públicos, cualquier parte del programa podría modificarlos libremente y romper dichas invariantes sin que la clase pudiera impedirlo. En cambio, si los atributos están encapsulados solo pueden cambiarse a través de setters o métodos controlados


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Respuesta
Una clase inmutable es aquella cuyo estado no puede cambiar una vez creada la instancia. Esto significa que todos sus atributos deben inicializarse en el constructor y, a partir de ese momento, ningún método puede modificarlos.

Un método modificador es cualquier método que cambia el estado interno de un objeto. Un setter es un caso particular de método modificador.
En las clases inmutables, directamente no existen métodos modificadores

En primer lugar, elimina la posibilidad de que otros componentes del programa alteren inadvertidamente el estado del objeto. 
Además, facilita la programación concurrente, ya que los objetos inmutables pueden compartirse sin riesgo de condiciones de carrera.
Tambien simplifica el diseño: al saber que el estado nunca cambia, resulta más fácil razonar, depurar y garantizar la estabilidad del código


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### Respuesta
Incluir un setter implica permitir que el estado interno del objeto pueda modificarse libremente desde el exterior, lo cual puede romper invariantes de clase.
En muchos casos, basta con exponer métodos de consulta (getters) y reservar la modificación del estado para métodos más específicos y controlados 


## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

### Respuesta

La clase String en Java es inmutable. Cada operación que parece alterar una cadena en realidad crea un objeto nuevo
Al concatenar dos cadenas, como en s = s + "hola";, se crea una nueva instancia de String que contiene el resultado de la concatenación. El objeto original no cambia, creando problemas de optimizacion.

Si se necesita construir paso a paso una cadena muy larga, lo recomendable es utilizar clases mutables como StringBuilder (o StringBuffer si se necesita sincronización). 
StringBuilder permite modificar el contenido sin crear objetos intermedios, acumulando las operaciones de forma eficiente.


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

### Respuesta

Los objetos pueden compararse por su identidad o por su contenido

La identidad se refiere a si dos variables apuntan al mismo objeto en memoria.En Java, el operador == compara siempre identidad.

El contenido implica comprobar si dos objetos distintos representan la misma información interna.El método equals en Java sirve precisamente para comparar contenido lógico entre objetos
Para comparar el contenido de dos cadenas se debe usar el método equals

```if (s1.equals(s2)) { ... }```


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

### Respuesta
Las clases wrapper son clases que encapsulan un valor de un tipo primitivo dentro de un objeto. Su finalidad es permitir tratar valores primitivos como objetos, de forma que puedan utilizarse en contextos donde solo se aceptan referencias.
En Java, cada tipo primitivo tiene su correspondiente clase wrapper (int → Integer, double → Double, boolean → Boolean, etc.),

La conversión entre un tipo primitivo y su wrapper puede realizarse de forma explícita creando un objeto con new, pero Java también ofrece un proceso automático llamado autoboxing y unboxing. 
Autoboxing convierte un primitivo en su wrapper correspondiente cuando el contexto lo requiere, mientras que unboxing hace lo contrario

Las clases wrapper ofrecen varias ventajas: permiten representar la ausencia de valor mediante null, integrarse con estructuras de datos orientadas a objetos y disponer de métodos utilitarios directamente asociados al valor (por ejemplo, Integer.parseInt)

Algunos lenguajes, como Python o Ruby, tratan todos los valores como objetos, por lo que no existe distinción entre primitivos y wrapper.

## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### Respuesta

Un tipo de dato enumerado en POO es un conjunto finito y predefinido de valores posibles que representan opciones claramente delimitadas. Se utiliza cuando una variable solo puede tomar uno de varios valores concretos y conocidos

En Java, un tipo enumerado (enum) es realmente una clase especial, aunque su sintaxis sea más compacta. Cada valor del enumerado es una instancia única y precreada de esa clase.

Los enumerados en Java ofrecen ventajas  en términos de encapsulación. 
Por un lado, limitan estrictamente los valores posibles, impidiendo que se creen nuevas instancias y evitando asignaciones no válidas. 
Por otro lado, permiten asociar comportamiento y datos internos a cada valor sin exponer detalles innecesarios al exterior


## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado. Añade además cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### Respuesta
public enum Mes {
    ENERO(31, 1),
    FEBRERO(28, 2),
    MARZO(31, 3),
    ABRIL(30, 4),
    MAYO(31, 5),
    JUNIO(30, 6),
    JULIO(31, 7),
    AGOSTO(31, 8),
    SEPTIEMBRE(30, 9),
    OCTUBRE(31, 10),
    NOVIEMBRE(30, 11),
    DICIEMBRE(31, 12);

    private final int dias;
    private final int numero;

    private Mes(int dias, int numero) {
        this.dias = dias;
        this.numero = numero;
    }

    public int getDias() {
        return dias; // Para FEBRERO se asume 28 días (sin contemplar años bisiestos)
    }

    public int getOrdinal() {
        return numero; // Equivalente a this.ordinal() + 1
    }

    public boolean esDePrimavera(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == MARZO || this == ABRIL || this == MAYO)
                : (this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE);
    }

    public boolean esDeVerano(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == JUNIO || this == JULIO || this == AGOSTO)
                : (this == DICIEMBRE || this == ENERO || this == FEBRERO);
    }

    public boolean esDeOtoño(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE)
                : (this == MARZO || this == ABRIL || this == MAYO);
    }

    public boolean esDeInvierno(boolean esHemisferioNorte) {
        return esHemisferioNorte
                ? (this == DICIEMBRE || this == ENERO || this == FEBRERO)
                : (this == JUNIO || this == JULIO || this == AGOSTO);
    }
}
