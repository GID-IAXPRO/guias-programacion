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

La encapsulación en POO busca que los datos internos de un objeto estén protegidos, de modo que no puedan modificarse de forma directa desde fuera de la clase. Esta idea supone que cada objeto controla su propio estado, exponiendo únicamente las operaciones necesarias para trabajar con él. La ocultación de información complementa esta idea al impedir que otros fragmentos de código accedan a detalles internos que no necesitan conocer para usar correctamente la clase. De esta manera, se evita que el estado interno sea modificado de forma incorrecta o inesperada.

Uno de los beneficios principales de la ocultación es la mejora en la seguridad y consistencia de los datos internos. Como el acceso se realiza siempre a través de métodos públicos (getters, setters o funciones bien definidas), la clase puede comprobar valores, aplicar validaciones o mantener invariantes antes de aceptar cualquier cambio. Otra ventaja importante es que se reduce la dependencia entre las distintas partes del programa: si algo externo no sabe cómo está implementado un atributo, entonces tampoco dependerá de ese detalle concreto. Esto permite cambiar la implementación interna más adelante sin afectar al código que ya funciona correctamente.

Además, la encapsulación facilita el mantenimiento, ya que cualquier error relacionado con el estado del objeto se localiza en una zona muy concreta: dentro de la propia clase. Del mismo modo, se mejora la claridad del diseño porque cada clase ofrece una interfaz pública limitada y previsiblemente más sencilla de entender que su funcionamiento completo. En conjunto, estos aspectos ayudan a que los programas orientados a objetos sean más robustos, más fáciles de adaptar y menos propensos a fallos derivados de accesos incorrectos.


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### Respuesta

La interfaz pública de una clase es el conjunto de métodos accesibles desde fuera y que permiten interactuar con el objeto. Representa lo que la clase “ofrece” al exterior y define cómo deben usarse sus operaciones, sin revelar cómo se implementan internamente. Gracias a esta interfaz, quien usa la clase solo necesita conocer las acciones disponibles, no los detalles de cómo se guardan o manipulan los datos.

La interfaz pública está directamente relacionada con la ocultación de información porque actúa como una barrera entre el exterior y la implementación interna. Todo aquello que no forma parte de la interfaz pública —atributos privados o métodos auxiliares— queda protegido frente a accesos directos. Esto ayuda a mantener el estado interno coherente y permite cambiar la implementación en el futuro sin afectar al código que utiliza la clase.


## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### Respuesta

La interfaz pública debe diseñarse con cuidado porque es la parte de la clase que utiliza el resto del programa. Si está mal estructurada, confusa o demasiado expuesta, puede obligar a otros módulos a interactuar de forma incorrecta o complicada, generando errores y dificultando el uso seguro de la clase. Una interfaz bien pensada permite que la clase se utilice de forma clara y controlada.

Cambiar una interfaz pública no suele ser fácil, ya que cualquier modificación afecta a todo el código que depende de ella. Si se cambia el nombre de un método, su comportamiento o sus parámetros, el resto del programa puede dejar de funcionar y necesitar cambios adicionales. Por eso, suele ser preferible mantener la interfaz estable y modificar solo la implementación interna, que está oculta y no afecta al exterior.


## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Respuesta

Las invariantes de clase son condiciones que siempre deben cumplirse para que un objeto se considere válido. Representan reglas internas que describen cómo debe mantenerse el estado de la clase para funcionar correctamente. Aunque durante la ejecución puedan existir momentos puntuales donde el estado no cumpla la invariante (por ejemplo, dentro de un método), al finalizar cualquier operación pública, la clase debe volver siempre a un estado coherente.

La ocultación de información ayuda a mantener estas invariantes porque evita que el código externo modifique directamente los atributos internos. Al forzar que todos los cambios pasen por métodos controlados, la clase puede verificar valores, impedir estados inválidos y asegurarse de que las reglas internas se respetan. Gracias a esto, el objeto mantiene estabilidad y se reduce el riesgo de errores provocados por modificaciones incontroladas desde fuera.


## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### Respuesta

```java
public class Punto {
    private double x;
    private double y;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    public double getX() { return x; }
    public double getY() { return y; }

    public void setX(double x) { this.x = x; }
    public void setY(double y) { this.y = y; }

    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    private double cuadrado(double v) {
        return v * v;
    }
}
```
Ocultación de información. La clase oculta su estado declarando x e y como private. De esta forma, el código externo no puede modificarlos directamente y cualquier cambio debe pasar por métodos públicos controlados (getters/setters), donde se podrían añadir validaciones si hiciera falta. Esto protege la coherencia del objeto y facilita mantener invariantes.

Interfaz pública de Punto. La interfaz pública está formada por los miembros accesibles desde fuera: public Punto(double x, double y), public double getX(), public double getY(), public void setX(double x), public void setY(double y) y public double calcularDistanciaAOrigen(). Estos métodos definen qué puede hacerse con la clase sin exponer cómo gestiona internamente sus datos.

Significado de public y private. public indica que un miembro es accesible desde cualquier código que pueda ver la clase; se utiliza para la interfaz pública (el “contrato” de uso). private limita el acceso al interior de la propia clase; se usa para ocultar detalles de implementación y proteger el estado interno frente a modificaciones no controladas.


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### Respuesta

En Java, los modificadores public y private pueden aplicarse principalmente a clases, atributos, métodos y constructores, dependiendo del nivel donde se encuentren. Estos modificadores permiten controlar qué partes del código son accesibles desde fuera de una clase o desde otros paquetes. En el caso de las clases, solo las clases de nivel superior pueden declararse public, mientras que las clases internas pueden declararse public o private, ya que forman parte del interior de otra clase.

En cuanto a los miembros de una clase —atributos, métodos y constructores—, tanto public como private pueden aplicarse sin restricciones. Declarar algo como public implica que es accesible desde cualquier otra clase del programa, mientras que private limita el acceso únicamente a la clase donde se declara. Esta capacidad de aplicar modificadores a los miembros es fundamental para implementar la encapsulación y controlar cómo se usa el estado interno del objeto.

Gracias a estos modificadores, Java permite decidir qué elementos deben formar parte de la interfaz pública de una clase y qué elementos deben permanecer ocultos como detalles internos. De esta manera, se facilita la protección del estado del objeto y se mejora la modularidad del programa al separar claramente lo que se expone y lo que se oculta.


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### Respuesta

En Programación Orientada a Objetos, aunque la distinción más conocida es entre visibilidad pública y privada, existen otros niveles de acceso que permiten controlar con mayor precisión quién puede utilizar determinados elementos de una clase. Estos niveles intermedios permiten un diseño más flexible, evitando exponer demasiado la implementación interna y manteniendo al mismo tiempo la posibilidad de colaboración entre clases relacionadas. La idea general es ofrecer distintas “capas” de accesibilidad para organizar mejor el código y sus dependencias.

En Java existen cuatro niveles de visibilidad: public, private, protected y el nivel por defecto (también llamado package-private). public permite acceso desde cualquier lugar, mientras que private restringe completamente el acceso a la clase donde se declara. protected permite acceso desde la misma clase, las subclases y las clases del mismo paquete, lo cual es útil para la herencia. El nivel por defecto, cuando no se especifica ningún modificador, restringe el acceso a las clases dentro del mismo paquete. Estos cuatro niveles permiten ajustar la visibilidad según las necesidades del diseño sin exponer más de lo necesario.

En otros lenguajes orientados a objetos existen variaciones. Por ejemplo, C++ ofrece public, private y protected, pero no tiene un nivel equivalente al package-private de Java; sin embargo, introduce otros mecanismos como friend que permiten accesos especiales entre clases concretas. Lenguajes como Python no tienen un sistema estricto de visibilidad, pero utilizan convenciones como el prefijo _ o __ para indicar que un atributo debería tratarse como privado. En conjunto, aunque los nombres y detalles varían, la mayoría de lenguajes proporcionan algún mecanismo para controlar la visibilidad más allá de lo público y lo privado.


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### Respuesta

En Java, los miembros private están ocultos para otras clases, pero no están ocultos para otras instancias de la misma clase cuando el acceso se realiza desde código de esa clase. Es decir, el modificador private limita el acceso por clase, no por objeto. Por ello, un método de Punto puede acceder a los campos privados x e y de cualquier instancia de Punto (incluida la instancia recibida por parámetro), pero una clase distinta no puede acceder a esos campos directamente.

Este comportamiento permite implementar operaciones “entre objetos” de forma natural manteniendo la encapsulación. Se puede, por ejemplo, calcular la distancia entre dos puntos usando internamente los private de ambos objetos, sin exponer esos atributos al exterior. De este modo, se preserva la ocultación de información frente a otras clases, mientras que las propias instancias de la clase colaboran a través de sus métodos.

```java
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

    // Acceso a privados de "otro" permitido por ser la MISMA clase
    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x; // válido: ambos "x" son private, pero dentro de Punto
        double dy = this.y - otro.y; // válido por el mismo motivo
        return Math.sqrt(dx * dx + dy * dy);
    }
}
```
En el ejemplo, calcularDistanciaAPunto accede a otro.x y otro.y aunque sean private, porque el acceso ocurre dentro del código de la clase Punto. Si se intentara leer p.x desde una clase distinta (por ejemplo, Main), el compilador lo impediría. Por tanto, la respuesta correcta es: los miembros privados están ocultos para otras clases (a), pero no para otras instancias si el acceso se realiza desde la misma clase (no para (b)).


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Respuesta

Los métodos getter y setter son funciones utilizadas para acceder y modificar los atributos privados de una clase de forma controlada. En lugar de permitir acceder directamente a las variables internas, la clase ofrece métodos públicos que devuelven el valor (get) o permiten cambiarlo (set). Esto sigue el principio de encapsulación, ya que el estado interno del objeto no se expone directamente y siempre se gestiona a través de operaciones bien definidas.

Los getters suelen tener un nombre del estilo getAtributo() y devuelven el valor del atributo correspondiente. Los setters, por su parte, tienen el formato setAtributo(nuevoValor) y permiten actualizar el estado del objeto. La utilidad principal de estos métodos es que permiten añadir controles adicionales, como validaciones, cálculos derivados o restricciones, antes de devolver o modificar el valor real. Así, se evita que el resto del programa manipule el estado interno de forma incorrecta o insegura.

Además, el uso de getters y setters contribuye a que la estructura interna de la clase pueda cambiar sin afectar a quienes la utilizan. Mientras la interfaz pública se mantenga, la implementación interna puede evolucionar libremente. Por este motivo, estos métodos son una herramienta fundamental en la programación orientada a objetos para mantener la modularidad y la protección del estado interno.


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### Respuesta

Cuando se afirma que la ocultación de información mejora la "seguridad" del programa, no se hace referencia a la seguridad informática en el sentido de evitar ataques o hackeos. En este contexto, la palabra “seguridad” se refiere a la protección del estado interno de un objeto frente a usos incorrectos por parte del propio programa. La ocultación permite que los atributos estén protegidos y solo puedan modificarse mediante métodos controlados, lo que reduce errores y comportamientos inesperados.

El objetivo principal de la ocultación es garantizar que los objetos mantengan siempre un estado coherente, evitando que otras partes del código cambien valores de forma accidental o inapropiada. De este modo, se previenen fallos lógicos y se facilita la tarea de mantener y depurar el programa. Esta forma de seguridad busca la robustez interna más que la defensa frente a amenazas externas.

Por tanto, aunque ambas estén relacionadas con evitar problemas, la ocultación de información no protege contra ataques externos, sino que ayuda a escribir programas más fiables, estructurados y resistentes a errores provocados por un mal uso de sus clases.


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### Respuesta

Un miembro de instancia es un atributo o método asociado a cada objeto concreto de una clase. Esto significa que cada instancia tiene su propia copia de los atributos, y el comportamiento puede depender del estado particular de ese objeto. Por ejemplo, en una clase Punto, cada objeto tiene su propio x e y, que pueden ser diferentes entre sí. Los métodos de instancia operan sobre los valores específicos de cada objeto, usando la referencia implícita this.

Por otro lado, un miembro de clase es un atributo o método marcado con static, lo que indica que pertenece a la clase en sí, y no a las instancias. Esto implica que existe una única copia compartida por todos los objetos de esa clase. Se utiliza para valores o comportamientos que no dependen del estado individual de cada instancia. Por ejemplo, un contador de objetos creados o una constante común a toda la clase pueden declararse como miembros de clase.

Los miembros de clase también pueden ocultarse utilizando los modificadores private, public o protected. Al igual que ocurre con los miembros de instancia, declarar un miembro de clase como private impide que otras clases accedan directamente a él, manteniéndolo como un detalle interno de la implementación. Esto permite mantener el control sobre valores compartidos y evitar que el exterior los modifique sin pasar por métodos públicos que gestionen su uso.


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Respuesta

Sí, en algunos casos tiene sentido que los constructores sean privados. Un constructor privado impide que otros creen objetos directamente desde fuera de la clase, lo que permite controlar completamente cómo y cuándo se crean las instancias. Esto resulta útil cuando no interesa que el usuario del código pueda construir objetos libremente, sino que debe hacerlo a través de métodos específicos que garanticen un uso correcto.

En resumen, aunque lo normal es que los constructores sean públicos, declararlos privados permite restringir la creación de objetos para asegurar un uso controlado y coherente de la clase.


## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### Respuesta

En Java, los miembros de clase se indican con la palabra clave static. Un miembro static pertenece a la clase en sí y no a cada objeto individual: existe una sola copia compartida por todas las instancias. Suelen usarse para constantes comunes, contadores globales o estado agregado que interesa mantener a nivel de clase. Para accederlos, se recomienda hacerlo con el nombre de la clase (por ejemplo, Punto.getMaxX()), aunque también pueden usarse desde una instancia.

A continuación, se muestra una versión de Punto que incorpora miembros de clase static para registrar los valores máximos de x e y que se hayan asignado a cualquier punto creado hasta el momento. Se actualizan desde el constructor y desde los setters, de forma que los máximos reflejen la última información global. Se exponen mediante getters estáticos públicos que forman parte de la interfaz de clase (no de instancia).

```java
public class Punto {
    // Estado de instancia (oculto)
    private double x;
    private double y;

    // Miembros de clase (compartidos por TODAS las instancias)
    private static double maxX = Double.NEGATIVE_INFINITY;
    private static double maxY = Double.NEGATIVE_INFINITY;

    // Constructor
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
        actualizarMaximos(x, y);
    }

    // Getters de instancia
    public double getX() { return x; }
    public double getY() { return y; }

    // Setters de instancia: actualizan máximos globales al cambiar valores
    public void setX(double x) {
        this.x = x;
        if (x > maxX) maxX = x;
    }

    public void setY(double y) {
        this.y = y;
        if (y > maxY) maxY = y;
    }

    // Operaciones de instancia
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x;
        double dy = this.y - otro.y;
        return Math.sqrt(dx * dx + dy * dy);
    }

    // --- Interfaz de CLASE (miembros estáticos públicos) ---
    public static double getMaxX() { return maxX; }
    public static double getMaxY() { return maxY; }

    // Detalle interno para centralizar la actualización
    private static void actualizarMaximos(double x, double y) {
        if (x > maxX) maxX = x;
        if (y > maxY) maxY = y;
    }
}
```


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

### Respuesta

```java
public static Punto fromRounded(double x, double y) {
    double rx = Math.round(x); // redondea al entero más cercano
    double ry = Math.round(y);
    return new Punto(rx, ry);
}
```
Si he usado static. Es un método factoría estático porque crea instancias de Punto sin requerir un objeto previo.


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### Respuesta

```java
public class Punto {
    // Implementación interna: array de dos posiciones [x, y]
    private final double[] coords = new double[2];

    // Constructor (misma firma pública)
    public Punto(double x, double y) {
        coords[0] = x; // x
        coords[1] = y; // y
    }

    // Getters (misma interfaz pública)
    public double getX() { return coords[0]; }
    public double getY() { return coords[1]; }

    // Setters (misma interfaz pública)
    public void setX(double x) { coords[0] = x; }
    public void setY(double y) { coords[1] = y; }

    // Operación de instancia (sin cambios en la interfaz)
    public double calcularDistanciaAOrigen() {
        double x = coords[0];
        double y = coords[1];
        return Math.sqrt(x * x + y * y);
    }

    // Puede acceder a los privados de otra instancia por ser la misma clase
    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.coords[0] - otro.coords[0];
        double dy = this.coords[1] - otro.coords[1];
        return Math.sqrt(dx * dx + dy * dy);
    }

    // (Opcional) método privado auxiliar, si se prefiere reutilizar lógica
    private static double cuadrado(double v) { return v * v; }
}
```


## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### Respuesta

Aunque un atributo tenga getter y setter públicos, no es recomendable declararlo público. Si el atributo fuese público, cualquier parte del programa podría modificarlo libremente sin restricciones, lo que impediría controlar los valores asignados y dificultaría mantener el estado del objeto en condiciones válidas. En cambio, manteniendo el atributo privado y proporcionando getters y setters, la clase conserva la posibilidad de validar datos, aplicar reglas internas o ejecutar lógica adicional antes de aceptar un cambio.

La convención más habitual en los lenguajes orientados a objetos, incluido Java, es que todos los atributos sean privados. Esto forma parte del principio de encapsulación: el estado interno del objeto debe estar protegido y solo debe exponerse a través de su interfaz pública, compuesta por métodos bien definidos. De esta forma, se evita que el resto del programa dependa directamente de la estructura interna de la clase, lo que facilita realizar cambios en la implementación sin afectar al código externo.

Esta decisión está directamente relacionada con las invariantes de clase. Al mantener los atributos como privados, la clase puede asegurarse de que cualquier modificación pase por métodos que verifiquen que el estado sigue siendo válido. Si los atributos fueran públicos, sería imposible garantizar que se respeten esas invariantes, ya que cualquier parte del programa podría colocar al objeto en un estado incorrecto. Por tanto, la encapsulación no solo mejora la claridad del diseño, sino que también protege la coherencia interna del objeto.


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Respuesta

Una clase se considera inmutable cuando, una vez creado un objeto, su estado interno no puede cambiarse. Esto implica que todos sus atributos deben inicializarse en el constructor y no debe existir ningún mecanismo que permita modificar esos valores posteriormente. En Java, esto suele conseguirse declarando los atributos como private y final, y no proporcionando métodos setter. De esta forma, cada objeto representa un valor fijo y estable a lo largo de toda su vida.

Un método modificador es cualquier método que cambia el estado interno de un objeto. Aunque los setters son el ejemplo más evidente, no son los únicos métodos que modifican el estado: cualquier método que altere atributos internos, incluso si no sigue la forma típica de un setter (por ejemplo, incrementarContador() o mover(double dx, double dy)), también se considera un modificador. Por lo tanto, un método modificador no es siempre un setter, aunque todos los setters sí son métodos modificadores.

Las clases inmutables tienen varias ventajas importantes. Al no poder modificarse después de crearse, se evita que sus objetos entren en estados incorrectos o inconsistentes, lo que mejora la robustness y facilita el razonamiento sobre el programa. También son naturalmente seguras frente a problemas de aliasing: si dos partes del programa comparten la misma instancia, no existe riesgo de que una cambie el estado inesperadamente para la otra. Además, las clases inmutables son más sencillas de usar en programación concurrente, ya que no requieren sincronización adicional al no haber modificaciones del estado compartido.


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### Respuesta

No es recomendable incluir métodos setter siempre ni como una convención general. Aunque los setters permiten modificar atributos de forma controlada, su presencia implica que el estado del objeto puede cambiar libremente desde el exterior, lo que no siempre es deseable. Añadir setters por defecto puede romper la encapsulación o permitir que el objeto entre en estados inválidos si no se gestionan adecuadamente. Por este motivo, se aconseja incluir setters únicamente cuando la lógica del diseño realmente necesite que esos atributos puedan modificarse.

En muchos casos, especialmente en clases que representan valores o entidades que deberían mantenerse estables, es preferible no ofrecer setters y limitar el acceso mediante getters o métodos más específicos. Esto permite un mayor control sobre las invariantes de clase y reduce el riesgo de modificaciones inesperadas o incorrectas. Además, al no exponer setters innecesarios, se permite que la implementación interna pueda evolucionar sin afectar al código que utiliza la clase.

Finalmente, restringir o evitar setters facilita el diseño de clases inmutables, que suelen ser más seguras, más sencillas de razonar y más robustas frente a errores o condiciones indeseadas. Por tanto, la inclusión de setters debe responder a una necesidad real dentro del diseño, y no a una convención automática.


## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

### Respuesta

En Java, la clase String es inmutable, lo que significa que una vez creada una cadena, su contenido no puede modificarse. Cada vez que se realiza una operación que parece modificar una cadena —por ejemplo, concatenar otra cadena— en realidad se está creando un nuevo objeto String, mientras que los anteriores permanecen sin cambios. Esta característica aporta seguridad y previsibilidad, pero también puede generar un coste de rendimiento si se realizan muchas concatenaciones seguidas.

Cuando se concatenan dos cadenas con el operador +, Java crea internamente un nuevo objeto String que contiene el resultado de la unión. Por ejemplo, en una operación como s = s + "a";, la cadena original no se modifica, sino que se crea una nueva y se asigna a s. Si esto se repite muchas veces, se generan múltiples objetos temporales, lo que puede resultar ineficiente en memoria y tiempo.

Cuando se necesita construir una cadena muy larga mediante concatenaciones repetidas, lo más recomendable es usar clases mutables, como StringBuilder o StringBuffer. Estas clases permiten modificar el contenido sin crear objetos nuevos en cada operación. Con StringBuilder, las concatenaciones se realizan de forma más eficiente y el rendimiento mejora notablemente, sobre todo en bucles o procesos donde se añaden muchas partes pequeñas a una cadena


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

### Respuesta

En Programación Orientada a Objetos, los objetos pueden compararse por identidad o por contenido. La identidad se refiere a si dos referencias apuntan al mismo objeto en memoria, mientras que el contenido compara si los valores internos de ambos objetos son equivalentes. En Java, el operador == solo compara la identidad (misma referencia), no el contenido, por lo que dos objetos distintos con los mismos valores se considerarían diferentes usando este operador.

El método equals en Java sirve para comparar objetos por contenido, y es un método heredado de la clase Object. Sin embargo, por defecto, su implementación es exactamente la misma que ==, es decir, compara las referencias y no los valores internos. Para que equals compare correctamente el contenido de una clase, es necesario sobrescribirlo en la implementación de esa clase, definiendo qué significa que dos objetos sean "iguales" según su estado interno.

En el caso concreto de las cadenas (String), Java ya sobrescribe el método equals para comparar el contenido del texto. Por ello, dos cadenas deben compararse siempre con equals, nunca con ==. El operador == solo indica si ambas referencias apuntan al mismo objeto, mientras que equals determina si contienen exactamente los mismos caracteres. De esta forma, la comparación de cadenas es correcta y no depende de su ubicación en memoria.


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

### Respuesta

Las clases wrapper son clases que permiten representar valores primitivos como objetos. En Java, tipos como int, double o boolean no son objetos, pero existen clases como Integer, Double o Boolean que envuelven estos valores para poder utilizarlos cuando se requiere un objeto. Esta conversión permite almacenar valores primitivos en estructuras que solo aceptan objetos, como colecciones (ArrayList, HashMap) o ciertas APIs que trabajan exclusivamente con referencias.

En Java, el uso de wrappers puede hacerse de forma manual, creando objetos explícitamente con algo como Integer i = new Integer(5);, aunque lo habitual es usar autoboxing, un proceso automático que convierte un primitivo en su correspondiente wrapper sin necesidad de llamar al constructor. Por ejemplo, escribir Integer x = 5; provoca que Java envuelva el número 5 en un objeto Integer. El proceso inverso, convertir un wrapper en un primitivo, se llama unboxing, y también se realiza automáticamente.

Las clases wrapper tienen varias ventajas. Permiten usar métodos adicionales asociados al tipo, facilitan su uso en colecciones y permiten representar casos especiales como valores nulos (null), algo que los tipos primitivos no pueden hacer. Además, algunos wrappers ofrecen funcionalidades adicionales, como constantes, conversión de cadenas y utilidades de comparación.

No todos los lenguajes orientados a objetos necesitan wrappers. Algunos lenguajes, como Python, no distinguen entre tipos primitivos y objetos: todo es un objeto desde el principio, por lo que no existe la necesidad de envolver valores simples en clases adicionales. Java, en cambio, mantiene tipos primitivos por motivos de eficiencia, lo que hace que las clases wrapper sean necesarias para combinar los beneficios del rendimiento con la flexibilidad del modelo orientado a objetos.


## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### Respuesta

Un tipo de dato enumerado es un tipo que permite representar un conjunto finito y cerrado de valores posibles, normalmente relacionados entre sí. Su objetivo es modelar situaciones en las que las opciones válidas están claramente limitadas, como los días de la semana, los estados de una máquina o los palos de una baraja. Al usar un tipo enumerado, el lenguaje garantiza que solo pueden utilizarse los valores permitidos, lo que evita errores y hace que el código sea más legible y seguro.

En Java, un tipo enumerado (enum) es realmente una clase especial, aunque el lenguaje ofrece una sintaxis más simple para declararlo. Internamente, cada valor del enum es una instancia única y predefinida de esa clase. Esto permite que los enumerados tengan atributos, métodos y comportamientos específicos, igual que cualquier otra clase, pero manteniendo su significado como conjunto de valores fijos.

Los enumerados en Java aportan ventajas importantes en términos de encapsulación. Al encapsular los valores válidos dentro del propio enum, se evita que el código externo pueda inventar valores que no tengan sentido. Además, es posible mantener la implementación interna oculta y exponer solo los valores y métodos que formen parte de la interfaz pública. Esto mejora la robustez del programa y evita inconsistencias, ya que la creación de nuevos valores queda completamente restringida y controlada por la propia construcción del enum.

## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado. Añade además cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### Respuesta

```java
public enum Mes {
    ENERO(1, 31), FEBRERO(2, 28), MARZO(3, 31),
    ABRIL(4, 30), MAYO(5, 31), JUNIO(6, 30),
    JULIO(7, 31), AGOSTO(8, 31), SEPTIEMBRE(9, 30),
    OCTUBRE(10, 31), NOVIEMBRE(11, 30), DICIEMBRE(12, 31);

    // Atributos privados (encapsulación)
    private final int ordinal;
    private final int dias;

    // Constructor privado del enum
    Mes(int ordinal, int dias) {
        this.ordinal = ordinal;
        this.dias = dias;
    }

    // Interfaz pública
    public int getDias() {
        return dias;
    }

    public int getOrdinal() {
        return ordinal; // 1..12 (diferente de enum.ordinal() que es 0..11)
    }

    public boolean esDePrimavera(boolean esHemisferioNorte) {
        if (esHemisferioNorte) {
            return this == MARZO || this == ABRIL || this == MAYO;
        } else {
            return this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE;
        }
    }

    public boolean esDeVerano(boolean esHemisferioNorte) {
        if (esHemisferioNorte) {
            return this == JUNIO || this == JULIO || this == AGOSTO;
        } else {
            return this == DICIEMBRE || this == ENERO || this == FEBRERO;
        }
    }

    public boolean esDeOtoño(boolean esHemisferioNorte) {
        if (esHemisferioNorte) {
            return this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE;
        } else {
            return this == MARZO || this == ABRIL || this == MAYO;
        }
    }

    public boolean esDeInvierno(boolean esHemisferioNorte) {
        if (esHemisferioNorte) {
            return this == DICIEMBRE || this == ENERO || this == FEBRERO;
        } else {
            return this == JUNIO || this == JULIO || this == AGOSTO;
        }
    }
}
```