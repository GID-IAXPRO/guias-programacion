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

### En la Programación Orientada a Objetos (POO), la **encapsulación** busca agrupar los datos (atributos) y los métodos (operaciones) que actúan sobre esos datos en una única unidad lógica llamada **clase**. Esto permite modelar entidades del mundo real como objetos autocontenidos, donde el estado y el comportamiento están estrechamente vinculados. Tiene que ver con "Protección". Evita estados no válidos de mis objetos. También evita dependencias desde fuera que no se quieren. Por su parte, la **ocultación de información** es el principio complementario que consiste en **restringir el acceso directo a los detalles internos** (implementación) de un objeto, exponiendo solo una **interfaz pública** controlada de métodos para interactuar con él. Mientras la encapsulación es el "cómo" se empaqueta, la ocultación es el "qué" se oculta y "por qué".

El objetivo principal de esta combinación es lograr un **acoplamiento bajo** entre diferentes partes del sistema. Al ocultar la implementación, se evita que el código cliente dependa de los detalles internos de una clase, los cuales pueden cambiar. Esto permite **modificar la implementación interna** de una clase (por ejemplo, cambiar el tipo de un atributo o la lógica de un algoritmo) sin afectar a ningún otro componente del programa que use esa clase, siempre que la interfaz pública (los métodos visibles) se mantenga constante.

Algunas ventajas clave de la ocultación de información son:
1.  **Modularidad y mantenibilidad**: Permite aislar cambios y razonar sobre partes del sistema de forma independiente.
2.  **Control de acceso y validez**: Los datos solo pueden modificarse a través de métodos públicos (como *setters*), lo que permite validar las entradas y mantener la **integridad** y consistencia del estado interno del objeto (por ejemplo, evitar que un `Punto` tenga coordenadas negativas si no es deseado).
3.  **Reducción de efectos secundarios**: Al prevenir que código externo modifique directamente los atributos, se eliminan modificaciones accidentales y errores difíciles de rastrear.
4.  **Flexibilidad y evolución del diseño**: Facilita la mejora, corrección o sustitución de componentes internos sin romper el código existente que depende de la clase, fomentando un diseño robusto y a prueba del futuro.


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### La **interfaz pública** de una clase es el conjunto de **métodos y atributos declarados como públicos** (los miembros), (`public`) a través de los cuales otros objetos pueden interactuar con ella desde fuera, es decir, los que no están ocultos. Define **qué puede hacer** el objeto (su contrato o comportamiento observable), pero **oculta cómo lo hace** (su implementación interna).

Se relaciona directamente con la ocultación de información porque actúa como una **barrera controlada**. Todo lo que está fuera de esta interfaz (atributos privados, métodos internos) está **oculto** y protegido de acceso externo directo. Esto permite cambiar la implementación interna con total libertad, siempre que se mantenga estable la interfaz pública que el resto del programa usa.


## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### Hay que diseñar con cuidado la interfaz pública porque **define el contrato estable** que el resto del sistema usará para interactuar con la clase. Una interfaz bien diseñada es clara, mínima y cumple un propósito cohesivo, lo que facilita su comprensión y uso correcto.

No es fácil cambiarla una vez el sistema está en desarrollo, especialmente si otras clases o módulos ya dependen de ella. Modificarla (cambiar nombres de métodos, parámetros o tipos de retorno) suele **romper el código cliente** existente, forzando cambios costosos en cascada. Por ello, la interfaz pública debe ser estable y pensada a largo plazo, mientras que la implementación interna puede evolucionar libremente. Si se cambia tiene más consecuencias que cualquier cambio en la parte oculta.


## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Las **invariantes de clase** son **condiciones o reglas lógicas** que deben cumplir y ser válidas para un objeto durante toda su vida (excepto durante la ejecución de un método). Definen un **estado interno consistente y válido**. Por ejemplo, para una clase `CuentaBancaria`, un invariante podría ser "el atributo `saldo` nunca debe ser negativo". Persona debe de tener edad >= 0.

La ocultación de información ayuda a **garantizar** estos invariantes. Al hacer los atributos privados y solo permitir su modificación a través de métodos públicos (como `ingresar()` o `retirar()`), la clase puede **validar y controlar** cada cambio de estado. Esto impide que código externo establezca directamente valores inválidos (ej: `cuenta.saldo = -100;`), protegiendo así la integridad del objeto y asegurando que los invariantes se mantengan siempre.


## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### ```java
public class Punto {
    // Atributos PRIVADOS: ocultación de información
    private double x;
    private double y;

    // Constructor PÚBLICO: parte de la interfaz
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Método público: parte de la interfaz
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
}


**`public`** y **`private`** son **modificadores de acceso**. `public` significa que el elemento (método o constructor) es **accesible desde cualquier otra clase**, formando parte de la **interfaz pública**. `private` significa que el elemento (generalmente atributos) solo es **accesible desde dentro de la propia clase**, quedando así oculto.

La **interfaz pública** de esta clase `Punto` está compuesta por: el **constructor** `Punto(double, double)`, el método `calcularDistanciaAOrigen()` y los métodos **getters** `getX()` y `getY()`. Estos son los únicos medios definidos para que el mundo exterior cree objetos `Punto` y obtenga información de ellos, cumpliendo así con la ocultación.


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### En Java, los modificadores `public` y `private` se pueden aplicar a **cuatro tipos de miembros** dentro de una clase: **atributos (variables de instancia)**, **métodos**, **constructores** y **clases internas**. Su propósito es controlar desde dónde se puede acceder a estos miembros.

El modificador `public` hace que un miembro sea **accesible desde cualquier otra clase** en cualquier paquete. El modificador `private` restringe el acceso para que el miembro sea **únicamente visible y utilizable dentro de la propia clase** donde se declara. No pueden aplicarse directamente a **variables locales** dentro de un método, ya que su ámbito ya está limitado al propio método por definición.

Su uso estratégico es la base de la ocultación de información. Los atributos suelen declararse `private` para proteger los datos, mientras que los métodos que componen la interfaz útil de la clase se declaran `public`. También es común tener constructores `public` y, en ciertos patrones de diseño, métodos auxiliares `private` que solo sirven de apoyo interno a la clase.


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### En POO existen más tipos de visibilidad. En **Java**, además de `public` y `private`, están **`protected`** y el **modificador por defecto (package-private)**. `protected` permite acceso desde la misma clase, clases del mismo paquete y cualquier subclase (heredera), solo se ve desde "subclase". El modificador por defecto (sin palabra clave) permite acceso solo desde clases del **mismo paquete**.

**Otros lenguajes tienen modelos distintos**. En **C++** existen `public`, `private`, `protected` y `friend` (que otorga acceso a funciones/clases específicas). En **C#** tiene niveles similares a Java, añadiendo `internal` (acceso dentro del mismo ensamblado) e `protected internal`. **Python** no tiene palabras clave para esto; por convención, un guion bajo `_` al inicio del nombre sugiere que un miembro es "privado", pero es solo una indicación, no una restricción del lenguaje.


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### Los miembros privados de un objeto están ocultos para **otras clases**, pero **son directamente accesibles por otras instancias de la misma clase**. Esto significa que un objeto puede acceder a los atributos `private` de otro objeto **si ambos son de la misma clase**.

Ejemplo con un método que calcula la distancia a otro punto:
```java
public class Punto {
    private double x;
    private double y;

    // ... constructor y otros métodos

    // Método que accede a los atributos PRIVADOS de otro objeto de su misma clase
    public double calcularDistanciaAPunto(Punto otro) {
        double difX = this.x - otro.x;   // Acceso directo a otro.x (privado)
        double difY = this.y - otro.y;   // Acceso directo a otro.y (privado)
        return Math.sqrt(difX * difX + difY * difY);
    }
}
```

**Explicación**: Dentro del método `calcularDistanciaAPunto`, el objeto actual (`this`) accede **directamente** a los atributos privados `otro.x` y `otro.y` del otro objeto `Punto` pasado como parámetro. Esto es posible porque el código está **dentro de la clase `Punto`**. La restricción `private` se aplica a nivel de **clase**, no de **objeto**. Por lo tanto, cualquier método de la clase `Punto` tiene acceso total a los miembros privados de *cualquier* instancia de `Punto`, no solo a los suyos propios.


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Los métodos **getter** y **setter** son métodos públicos que proporcionan **acceso controlado** a los atributos privados de una clase para obtener su valor o cambiarlo. Un **getter** (o *accesor*) **devuelve el valor** de un atributo privado. Un **setter** (o *mutador*) **modifica el valor** de un atributo privado, pudiendo incluir validaciones.

Son un mecanismo fundamental de la encapsulación. En lugar de exponer los atributos directamente como públicos, se ofrecen estos métodos como parte de la interfaz. Esto permite **validar datos** (ej: impedir valores negativos), **controlar cambios** (ej: notificar a otros componentes) o **calcular valores on-demand** (ej: edad a partir de fecha de nacimiento), manteniendo oculta la representación interna.

Un ejemplo para la clase `Punto`:
```java
public double getX() { return x; } // Getter: solo lectura
public void setX(double x) { this.x = x; } // Setter: modificación simple
```


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### No, esto no es ciberseguridad, es facilitar una programación con menos bugs, normalmente no se refiere a seguridad contra hackers o ataques externos. La "seguridad" en este contexto se refiere a la **integridad y consistencia interna** del programa y al **control de acceso** dentro del propio código.

La mejora es principalmente de **diseño y mantenimiento**. Al restringir el acceso directo a los datos internos, se evita que otras partes del programa (escritas por otros desarrolladores o por uno mismo) **modifiquen accidentalmente el estado de un objeto de forma inconsistente o inválida**. Por ejemplo, se impide que se asigne un valor negativo al saldo de una `CuentaBancaria` si no pasa por un método `retirar()` que valide la operación. Esto **previene errores** y hace que el comportamiento del programa sea más predecible y fácil de razonar, lo que a su vez reduce "bugs".

En resumen, es una **seguridad a nivel de abstracción del software**, no de ciberseguridad. Aunque indirectamente un diseño robusto y libre de errores puede hacer que un sistema sea menos propenso a ciertas vulnerabilidades, el objetivo principal es garantizar la **correcta ejecución** y facilitar la **evolución** del código.


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### La diferencia fundamental es que un **miembro de instancia** (atributo o método no estático) pertenece a **cada objeto individual** (instancia) creado a partir de la clase, no son compartidos. En métodos no hay this. Cada instancia tiene su propia copia de los atributos de instancia y los métodos operan sobre el estado de ese objeto concreto. En cambio, un **miembro de clase** (atributo o método declarado con `static`) pertenece a la **clase en sí misma**, es compartido por todas las instancias y existe incluso si no se crea ningún objeto, no está asociado a ninguna instancia.

**Sí, los miembros de clase también se pueden y deben ocultar** aplicando los mismos modificadores de acceso (`private`, `protected`). Un atributo `static` privado es común para toda la clase pero solo es accesible desde dentro de ella, típicamente usado para constantes (`private static final`) o contadores internos compartidos. Un método `static` privado sirve como función auxiliar interna de la clase. La ocultación protege estos miembros compartidos del mismo modo que protege el estado de los objetos individuales.


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Sí, tiene sentido en situaciones específicas donde se quiere **controlar estrictamente cómo y cuándo se crean instancias** de una clase. Es un patrón de diseño útil, no un error.

Los casos más comunes son:
1.  **Clases utilitarias o de constantes**: Una clase que solo agrupa métodos estáticos (`Math`) o constantes (`public static final`). Un constructor privado impide la instanciación, forzando el uso directo de la clase (ej: `Math.sqrt()`).
2.  **Patrón Singleton**: Garantiza que una clase tenga **una única instancia** en todo el programa. El constructor es privado y se proporciona un método estático público (`getInstance()`) que controla la creación y devuelve siempre el mismo objeto.
3.  **Patrón Factory Method**: La creación de objetos se delega a un método estático público de la propia clase (un "método fábrica"), que puede tener un nombre más descriptivo, realizar lógica compleja antes de la construcción o devolver subclases diferentes. El constructor privado obliga a usar este método.
- Un constructor auxiliar oculto, llamado desde otros constructores públicos.
- Cuando prefiero usar métodos factoría.
- Cuando quiero controlar el número de instancias.

## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### Los **miembros de clase** en Java se indican con la palabra clave **`static`**. Se declaran dentro de la clase, pero fuera de cualquier método.

Ejemplo en la clase `Punto` con miembros de clase para rastrear los valores máximos:
```java
public class Punto {
    private double x, y;

    // Miembros de CLASE (static): compartidos por todas las instancias
    private static double maxX = Double.MIN_VALUE; // Máximo X global
    private static double maxY = Double.MIN_VALUE; // Máximo Y global

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
        // Actualizar máximos al crear un nuevo punto
        if (x > maxX) maxX = x;
        if (y > maxY) maxY = y;
    }

    // Métodos de CLASE (static) para consultar los máximos
    public static double getMaxX() { return maxX; }
    public static double getMaxY() { return maxY; }

    // ... resto de métodos de instancia (getters, distancia, etc.)
}
```

**Uso y explicación**:
```java
Punto p1 = new Punto(5.0, 3.0);
Punto p2 = new Punto(9.0, 1.0);

// Acceso a miembros de clase usando el nombre de la clase
System.out.println("Máximo X global: " + Punto.getMaxX()); // 9.0
System.out.println("Máximo Y global: " + Punto.getMaxY()); // 3.0
```
Los atributos `maxX` y `maxY` son `static`, por lo que **existe una única copia** en memoria compartida por todos los objetos `Punto`. Cada vez que se crea un nuevo punto (constructor), estos valores se actualizan si las nuevas coordenadas son mayores. Los métodos `getMaxX()` y `getMaxY()` también son `static`, por lo que se invocan directamente sobre la clase (`Punto.getMaxX()`) para consultar estos máximos globales, sin necesidad de un objeto concreto. Los máximos están encapsulados como `private static` y solo se exponen mediante getters estáticos públicos.


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

### ```java
public static Punto crearPuntoRedondeado(double x, double y) {
    return new Punto(Math.round(x), Math.round(y));
}

**Sí, se ha declarado con `static`.** Es un **método de clase** porque su lógica no depende del estado de ningún objeto `Punto` en particular. Su función es crear y devolver una nueva instancia, por lo que debe poder invocarse directamente desde la clase, por ejemplo: `Punto p = Punto.crearPuntoRedondeado(3.7, 4.2);


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### ```java
public class Punto {
    // Implementación interna cambiada: array privado
    private double[] coordenadas = new double[2]; // índice 0: x, índice 1: y

    // La interfaz pública SE MANTIENE IGUAL
    public Punto(double x, double y) {
        this.coordenadas[0] = x;
        this.coordenadas[1] = y;
    }

    // Getters: la interfaz no cambia
    public double getX() { return this.coordenadas[0]; }
    public double getY() { return this.coordenadas[1]; }

    // Setters (si existieran): la interfaz no cambia
    public void setX(double x) { this.coordenadas[0] = x; }
    public void setY(double y) { this.coordenadas[1] = y; }

    // Métodos como calcularDistanciaAOrigen usan la nueva implementación interna
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(this.getX() * this.getX() + 
                         this.getY() * this.getY());
    }

    // ... El resto de métodos públicos (distanciaAPunto, etc.) 
    // se adaptan internamente para usar 'coordenadas[0]' y 'coordenadas[1]'
}

**Explicación clave**: La **interfaz pública** (constructores, métodos `getX()`, `getY()`, `calcularDistanciaAOrigen()`) **no se modifica**. El código cliente que usa la clase **no necesita ningún cambio** y ni siquiera es consciente de que internamente ahora se usa un array. Esto demuestra la ventaja principal de la ocultación de información: se puede **cambiar radicalmente la implementación interna** (de dos variables a un array) sin afectar a las demás partes del programa, siempre que se mantenga el contrato de la interfaz pública.


## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### No es mejor declararlo público, aunque superficialmente parezca equivalente. La diferencia crucial es el **control**. Un atributo público permite acceso directo y sin restricciones. Además para poder garantizar la variante de clase. Un getter/setter es un **punto de control** donde se puede añadir validación, lógica (como notificaciones), cambiar la representación interna o hacer el atributo de solo lectura (omitir el setter).

La convención más estricta y habitual en Java (y POO en general) es que **los atributos deben ser siempre privados** y emplea métodos de acceso. Este es un principio de diseño robusto, no solo una sugerencia. Los getters/setters se proporcionan solo cuando es necesario para la interfaz pública.

Esto tiene **todo que ver con las invariantes de clase**. Si un atributo es público, cualquier código externo puede ponerlo en un estado inválido, rompiendo los invariantes. Un setter privado permite **validar** el nuevo valor antes de asignarlo (ej: lanzar una excepción si es negativo) y así garantizar que el invariante se mantenga. Un getter puede incluso calcular o formatear el dato al devolverlo, sin alterar la representación interna.


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Una clase **inmutable** es aquella cuyos **objetos no pueden modificar su estado interno** después de ser creados. Todos sus atributos son `final` (o equivalentemente, no hay métodos que los cambien). Si se necesita un objeto con un valor diferente, se debe crear uno nuevo.

Un **método modificador** es cualquier método que **altera el estado interno** de un objeto (como un `setter`). No todos los métodos modificadores son setters: un método `aumentarSaldo(double cantidad)` es modificador pero tiene lógica adicional. Sí, un **setter es siempre un método modificador**, ya que su único propósito es cambiar un atributo.

**Ventajas de la inmutabilidad**:
1.  **Seguridad y simplicidad**: Los objetos no cambian, por lo que son **seguros para compartir** entre hilos (thread-safe) sin sincronización y su comportamiento es predecible.
2.  **Fiabilidad**: Se garantiza que los invariantes de clase se mantendrán durante toda la vida del objeto.
3.  **Facilita el razonamiento**: Al no haber cambios de estado ocultos, el código es más fácil de entender y depurar.
4.  -No hacer clases mutables como primera opción

Ejemplo de `Punto` inmutable en Java:
```java
public final class Punto { // Clase final para evitar herencia que la modifique
    private final double x; // Atributos final
    private final double y;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }
    // Solo getters, NO setters
    public double getX() { return x; }
    public double getY() { return y; }
}
```


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### No, **no es recomendable incluir setters siempre y como convención automática**. Crear setters para todos los atributos por defecto rompe el principio de encapsulación y puede llevar a un diseño deficiente.

La decisión debe basarse en el **diseño de la clase y su semántica**. Se deben proporcionar setters solo cuando tenga sentido que el **estado del objeto pueda cambiar de forma controlada** después de su creación. Para muchas clases, especialmente aquellas que representan valores (como `Punto`, `Fecha`, `Dinero`) o entidades con identidad, los setters pueden ser inapropiados o incluso peligrosos, ya que permitirían poner el objeto en un estado inválido o inconsistente.

**Alternativas y buenas prácticas**:
1.  **Clases inmutables**: No usar setters. Si se necesita una "modificación", crear y devolver una **nueva instancia** con los valores cambiados (ej: `punto.conX(5.0)` devuelve un nuevo `Punto`).
2.  **Validación en setters**: Si son necesarios, deben **validar** los valores para mantener las invariantes de clase.
3.  **Métodos con semántica**: En lugar de `setSaldo()`, usar métodos como `ingresar()` o `retirar()` que encapsulan la lógica de negocio.
4.  **Inicialización en el constructor**: Muchos atributos pueden y deben ser establecidos solo en el constructor, sin necesidad de ser modificados después.

La convención real es: **los atributos son siempre privados, y los getters/setters se proporcionan solo si son necesarios para el comportamiento diseñado de la clase**.


## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

La clase **`String` en Java es inmutable**. Una vez creado un objeto `String`, su secuencia de caracteres **no puede modificarse**. Métodos como `toUpperCase()` o `concat()` **no cambian la cadena original**, sino que **devuelven una nueva cadena** con el resultado.

Al concatenar dos cadenas con el operador `+` (ej: `"Hola" + "Mundo"`), el compilador internamente crea un **nuevo objeto `String`** que contiene la unión de ambas, dejando las originales intactas. Si esto se hace repetidamente en un bucle, se generan muchos objetos intermedios que son inmediatamente descartados, lo cual es **ineficiente en memoria y rendimiento**.

Para construir una cadena larga paso a paso de forma eficiente, se debe usar la clase **`StringBuilder`** (o `StringBuffer` para entornos multi-hilo). Estas clases son **mutables** y están diseñadas específicamente para esta tarea. Su método `append()` modifica la cadena interna sin crear nuevos objetos en cada operación, y al final se obtiene el resultado con `toString()`.

**Ejemplo correcto para muchas concatenaciones**:
```java
StringBuilder builder = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    builder.append("texto").append(i);
}
String resultado = builder.toString(); // Una sola cadena final
```


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java?

### En POO, los objetos se pueden comparar de dos formas fundamentales: **por identidad** y **por contenido (equivalencia)**. La **identidad** se refiere a si dos referencias apuntan **exactamente al mismo objeto** en memoria (`a == b`). La **equivalencia** se refiere a si dos objetos **distintos** tienen un **estado interno considerado igual** (valor de los atributos) según la lógica de la clase (ej: dos puntos con las mismas coordenadas).

En Java, el método **`equals(Object obj)`** está diseñado para **comparar objetos por su equivalencia de contenido**. Su implementación por defecto, heredada de la clase `Object`, **compara solo por identidad** (usa `==`), excepto en clases concretas donde se implementa una comparación por contenido, y ej en String. Por tanto, para que `equals` compare por contenido, debe ser **sobrescrito** en la clase, definiendo qué atributos la hacen equivalente.

**Para comparar dos cadenas (`String`) en Java, se debe usar siempre `equals()`**, no el operador `==`. La clase `String` tiene sobrescrito `equals()` para comparar el secuencia de caracteres. El operador `==` compararía solo si son el mismo objeto en memoria, lo que daría resultados incorrectos en la mayoría de casos, aunque las cadenas contengan el mismo texto.

**Uso correcto**:
```java
String a = new String("hola");
String b = new String("hola");
System.out.println(a.equals(b)); // true (mismo contenido)
System.out.println(a == b);      // false (no es el mismo objeto)
```


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers?

### Las **clases "wrapper"** (envoltorio) son clases que **encapsulan un tipo de dato primitivo** (como `int`, `double`) dentro de un objeto. En Java, son `Integer` para `int`, `Double` para `double`, `Boolean` para `boolean`, `Character` para `char`, etc. Su propósito es permitir tratar valores primitivos como objetos cuando el contexto lo requiere. 

Ocurren en lenguajes que tienen tipos primitivos, como en Java, mientras que otros lenguajes no tienen tipos primitivos como Python.

Se pueden crear explícitamente con el constructor (ej: `Integer i = new Integer(42);`), pero Java proporciona **autoboxing** y **unboxing**, procesos automáticos que convierten entre primitivos y sus wrappers de forma transparente. El *autoboxing* convierte automáticamente un primitivo a su wrapper (ej: `Integer i = 42;`), y el *unboxing* realiza la conversión inversa (ej: `int j = i;`).

**Ventajas principales**:
1.  **Permiten usar primitivos en contextos que requieren objetos**, como colecciones (`ArrayList<Integer>`) o genéricos.
2.  **Proporcionan funcionalidad adicional** a través de métodos estáticos (ej: `Integer.parseInt()`, `Double.isNaN()`).
3.  **Autoboxing/Unboxing**

**No todos los lenguajes tienen tipos primitivos y wrappers**. En Java y C# existen por razones históricas de eficiencia. En cambio, en lenguajes como **Python** o **JavaScript**, todos los datos (incluidos números y booleanos) son **objetos** desde el principio, por lo que no necesitan wrappers. En **C++**, no existe esta distinción: los tipos básicos no tienen wrappers; se pueden usar plantillas (`template`) directamente con ellos.


## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### Un **tipo de dato enumerado** es un tipo que define un **conjunto fijo de constantes con nombre**, representando todos los valores posibles que una variable de ese tipo puede tomar. Se usa para mejorar la legibilidad y seguridad del código, reemplazando "números mágicos" o cadenas.

En Java, **sí, un `enum` es una clase especial**, cuyas instancias son finitas conocidas de antemano, y tienen un nombre cada una (valor del enumerado). Se declara con la palabra clave `enum`, pero el compilador la traduce a una clase que extiende `java.lang.Enum`. Puede tener atributos, métodos, constructores (siempre privados) e implementar interfaces, pero no puede heredar de otra clase.

**Ventajas en términos de encapsulación**:
1.  **Seguridad de tipos**: El compilador garantiza que solo se usen las constantes definidas, evitando valores inválidos. Por ejemplo, un `enum Dia { LUNES, MARTES... }` solo acepta esos valores, no cualquier cadena o número.
2.  **Comportamiento asociado**: Los valores enumerados pueden encapsular datos y comportamientos específicos. Por ejemplo:
    ```java
    public enum Planeta {
        MERCURIO(3.303e+23, 2.4397e6);
        
        private final double masa;
        private final double radio;
        
        Planeta(double masa, double radio) { // Constructor privado implícito
            this.masa = masa;
            this.radio = radio;
        }
        public double getMasa() { return masa; } // Getter encapsulado
    }
    ```
3.  **Instancias controladas**: La clase `enum` garantiza que solo existen las instancias definidas en su declaración, actuando como un **Singleton** para cada constante. No se pueden crear instancias adicionales desde fuera, lo que protege la integridad del conjunto de valores.


## 23. Crea un tipo enumerado en Java que se llame Mes, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado.

## Respuesta sobre el Tipo Enumerado Mes en Java

Para implementar un tipo enumerado llamado `Mes` en Java que cumpla con los requisitos especificados, se debe crear una enumeración que contenga los doce meses del año. La encapsulación se aplica mediante la declaración de atributos privados que almacenen información relevante para cada mes, como su número de días y su posición ordinal en el año. Estos atributos deben ser definidos como campos privados dentro de la enumeración, lo que garantiza que solo puedan ser accedidos a través de los métodos públicos que se proporcionen.

La implementación requiere que cada constante del enumerado invoque un constructor privado que reciba los valores específicos para cada mes. Por ejemplo, `ENERO` puede construirse con 31 días y ordinal 1, mientras que `FEBRERO` se construiría con 28 días (o 29 para año bisiesto, aunque en este caso se puede optar por 28 como valor estándar) y ordinal 2. Este enfoque permite que cada instancia del enumerado encapsule sus propios datos, manteniendo la coherencia y la seguridad de la información.

```java
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
    private final int ordinal;
    
    private Mes(int dias, int ordinal) {
        this.dias = dias;
        this.ordinal = ordinal;
    }
    
    public int getDias() {
        return this.dias;
    }
    
    public int getOrdinal() {
        return this.ordinal;
    }
}
```

Para proporcionar acceso controlado a los atributos encapsulados, se deben implementar métodos públicos observadores (getters) que devuelvan los valores almacenados. El método `getDias()` retorna la cantidad de días del mes, mientras que `getOrdinal()` devuelve su posición numérica en el año. Estos métodos actúan como interfaz controlada hacia los datos internos, manteniendo el principio de encapsulación al no permitir modificaciones directas de los atributos. Además, el uso de atributos marcados como `final` asegura que los valores asignados durante la construcción no puedan ser alterados posteriormente, lo que refuerza la inmutabilidad y consistencia de cada instancia del enumerado.

## 24. Añade a la clase Mes del ejercicio anterior cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro enHemisferioNorte). Es decir: esDePrimavera(boolean esHemisferioNorte), esDeVerano(boolean esHemisferioNorte), esDeOtoño(boolean esHemisferioNorte), esDeInvierno(boolean esHemisferioNorte).

## Ampliación del Tipo Enumerado Mes con Métodos de Estación

Para incorporar la funcionalidad que determina si un mes pertenece a una estación específica según el hemisferio, se deben añadir cuatro métodos booleanos a la enumeración `Mes`. Cada método recibirá un parámetro `boolean` que indica si la evaluación debe realizarse para el hemisferio norte (`true`) o para el hemisferio sur (`false`). La lógica interna debe contemplar la distribución de las estaciones en cada hemisferio, considerando que los meses que abarcan cada estación son opuestos entre ambos hemisferios.

En el hemisferio norte, la primavera comprende marzo, abril y mayo; el verano incluye junio, julio y agosto; el otoño abarca septiembre, octubre y noviembre; mientras que el invierno corresponde a diciembre, enero y febrero. Para el hemisferio sur, esta distribución se invierte completamente: la primavera ocurre en septiembre, octubre y noviembre; el verano en diciembre, enero y febrero; el otoño en marzo, abril y mayo; y el invierno en junio, julio y agosto. Esta relación de opuestos debe reflejarse en la implementación mediante condicionales que evalúen el hemisferio solicitado.

```java
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
    private final int ordinal;
    
    private Mes(int dias, int ordinal) {
        this.dias = dias;
        this.ordinal = ordinal;
    }
    
    public int getDias() {
        return this.dias;
    }
    
    public int getOrdinal() {
        return this.ordinal;
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
    
    public boolean esDeInvierno(boolean enHemisferioNorte) {
        if (enHemisferioNorte) {
            return this == DICIEMBRE || this == ENERO || this == FEBRERO;
        } else {
            return this == JUNIO || this == JULIO || this == AGOSTO;
        }
    }
}
```

La implementación presentada utiliza comparaciones directas con las constantes del enumerado para determinar la pertenencia a una estación. Cada método encapsula la lógica específica según el hemisferio, devolviendo `true` únicamente cuando el mes actual coincide con los meses que constituyen la estación consultada. Esta aproximación mantiene la legibilidad del código y facilita su mantenimiento, ya que las condiciones están claramente expresadas mediante la comparación de instancias. Además, al tratarse de métodos de instancia, cada objeto `Mes` puede responder adecuadamente a las consultas sobre su pertenencia a las distintas estaciones, proporcionando una interfaz coherente y bien encapsulada para esta funcionalidad estacional.
