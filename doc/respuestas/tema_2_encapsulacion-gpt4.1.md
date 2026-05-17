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

La encapsulación y la ocultación de información son conceptos fundamentales en POO que buscan agrupar los datos (atributos) y las operaciones (métodos) que operan sobre ellos dentro de una misma entidad (la clase). La ocultación de información consiste en restringir el acceso directo a los detalles internos de un objeto, permitiendo que solo ciertos métodos públicos interactúen con el exterior. Esto es especialmente importante cuando se viene de C/C++ procedural, donde los datos y funciones están separados, por lo que en Java se logra una mayor cohesión.

Entre las principales ventajas de la ocultación de información se encuentran: (1) el control sobre cómo se modifican los datos internos, garantizando que siempre permanezcan en un estado válido; (2) la independencia del usuario del objeto respecto a cómo se implementa internamente, lo que permite cambiar la implementación sin afectar el código cliente; (3) la prevención de usos inadecuados o erróneos del objeto, ya que no todas las operaciones posibles sobre los datos internos son permitidas; y (4) la protección contra modificaciones no autorizadas, creando una barrera entre el mundo exterior y la estructura interna del objeto.

## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### Respuesta

La interfaz pública de una clase es el conjunto de métodos y atributos que están declarados como `public` y que, por tanto, son accesibles desde cualquier parte del programa. Es el "contrato" que la clase ofrece al exterior, especificando qué operaciones pueden realizar otros objetos sobre ella. Por ejemplo, en una clase `Punto`, la interfaz pública podría incluir métodos como `getX()`, `setX(double valor)` y `calcularDistanciaAOrigen()`, sin revelar cómo se almacenan internamente las coordenadas.

La interfaz pública está directamente relacionada con la ocultación de información porque define exactamente qué partes del objeto son visibles y accesibles. Los atributos y métodos privados quedan ocultos tras esta interfaz pública, creando una abstracción. Esto permite que el usuario del objeto solo interactúe a través de los métodos públicos diseñados, sin poder acceder o modificar directamente los detalles internos, lo que es especialmente útil para garantizar que los datos siempre permanezcan en un estado consistente.


## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### Respuesta

La interfaz pública de una clase debe diseñarse cuidadosamente porque una vez que ha sido publicada y utilizada por otros programas o módulos, cualquier cambio en ella romperá la compatibilidad con el código cliente. Cambiar o eliminar un método público, alterar sus parámetros, o modificar su comportamiento esperado puede hacer que código escrito por otros deje de funcionar. Esto es especialmente crítico en bibliotecas o componentes que serán utilizados por múltiples proyectos.

No es fácil cambiar la interfaz pública una vez establecida, especialmente si el código ya está en producción o en manos de otros desarrolladores. Por ello, debe planearse con anticipación, considerando qué métodos realmente necesitan ser públicos y cuáles deberían ser privados. Una buena práctica es mantener la interfaz pública lo más simple y estable posible, permitiendo agregar nuevos métodos públicos cuando sea necesario, pero evitando cambios que modifiquen o rompan lo ya existente.



## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Respuesta

Las invariantes de clase son propiedades o restricciones que deben ser verdaderas en todo momento para que un objeto se encuentre en un estado válido. Por ejemplo, en una clase que representa un círculo, la invariante podría ser que el radio siempre debe ser mayor que cero. Estas invariantes definen las reglas que garantizan la consistencia interna del objeto, asegurando que no llegue nunca a un estado "roto" o inconsistente que podría causar errores.

La ocultación de información es fundamental para mantener las invariantes de clase, ya que los datos privados solo pueden ser modificados a través de métodos públicos que el programador ha diseñado específicamente para mantener la validez del objeto. Si los atributos fueran públicos (como se haría en C procedural con estructuras), cualquier parte del código podría modificarlos directamente, violando potencialmente las invariantes. Por ello, al controlar el acceso a través de métodos como setters, se puede verificar que los nuevos valores cumplan con las restricciones antes de actualizar el estado interno del objeto.



## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### Respuesta

A continuación se presenta una clase `Punto` que utiliza ocultación de información:

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
    
    public void setX(double x) {
        this.x = x;
    }
    
    public void setY(double y) {
        this.y = y;
    }
    
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
}
```

La interfaz pública de la clase `Punto` está compuesta por el constructor y los cinco métodos públicos: `getX()`, `getY()`, `setX()`, `setY()` y `calcularDistanciaAOrigen()`. Estos son los únicos métodos con los que el código externo puede interactuar. El modificador `public` indica que esos métodos son visibles y accesibles desde cualquier lugar del programa; en cambio, `private` marca los atributos `x` e `y` como privados, lo que significa que solo pueden ser accedidos desde dentro de la clase misma. Esto es similar a las funciones estáticas en C/C++, que limitan la visibilidad, pero aquí se aplica a nivel de clase.


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### Respuesta


En Java, los modificadores `public` y `private` se pueden aplicar tanto a atributos (variables miembro) como a métodos de una clase. También se pueden aplicar a las clases mismas: una clase puede ser declarada como `public` (accesible desde cualquier paquete) o ser paquete-privada por defecto (si no se escribe ningún modificador). Adicionalmente, aunque menos comúnmente, se pueden aplicar a constructores, permitiendo así controlar cómo se crean instancias de una clase.

No obstante, hay limitaciones en su uso: las clases de nivel superior solo pueden ser `public` o paquete-privadas (no `private`), aunque las clases internas anidadas sí pueden ser `private`. Además, existen otros modificadores de visibilidad en Java como `protected` (que verá en temas posteriores), que permiten mayor control sobre quién puede acceder a cada miembro. Esto es más flexible que C/C++ puro, donde la visibilidad se controla más a nivel de archivo con palabras clave como `static`.


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### Respuesta


Además de la visibilidad pública y privada, existen otros niveles de visibilidad. En Java específicamente, hay cuatro niveles: `public` (accesible desde cualquier lugar), `private` (accesible solo dentro de la clase), `protected` (accesible dentro de la clase, el paquete y las subclases) y paquete-privado (cuando no se especifica ningún modificador, accesible dentro del paquete solamente). El nivel `protected` será más relevante cuando se estudie herencia y polimorfismo.

Otros lenguajes orientados a objetos tienen variaciones en estos niveles de visibilidad. Por ejemplo, Python utiliza convenciones de nomenclatura (con guiones bajos) en lugar de palabras clave explícitas para indicar privacidad, C++ tiene `public`, `private` y `protected`, y algunos lenguajes como Kotlin incluso tienen niveles adicionales como `internal` para restringir la visibilidad a un módulo específico. La idea común es que el programmador pueda controlar el nivel de exposición de cada miembro según sus necesidades de encapsulación.


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### Respuesta


La respuesta correcta es (a): Los miembros privados están ocultos para otras clases. Dentro de la misma clase, todos los métodos pueden acceder a los miembros privados de cualquier instancia, incluso si se trata de otro objeto. Esto es una característica importante de Java que permite que los métodos de una clase trabajen entre sí sin restricciones.

Esto se puede ilustrar con un método que calcula la distancia entre dos puntos:

```java
public double calcularDistanciaAPunto(Punto otro) {
    double dx = this.x - otro.x;  // Acceso permitido a x de otra instancia
    double dy = this.y - otro.y;  // Acceso permitido a y de otra instancia
    return Math.sqrt(dx * dx + dy * dy);
}
```

En este método, aunque `x` e `y` son privados, el código puede acceder directamente a `otro.x` e `otro.y` porque estamos dentro de la clase `Punto`. La privacidad protege contra acceso desde fuera de la clase, no entre instancias de la misma clase. Por ello, diseñar la interfaz pública es crucial: es la barrera que protege a los objetos de otras clases, no de otros objetos de su propia clase.


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Respuesta


Los métodos getter y setter son métodos públicos ampliamente utilizados en POO para leer y modificar el valor de atributos privados. Un getter es un método público que retorna el valor de un atributo privado, permitiendo que código externo consulte su valor sin poder modificarlo directamente. Por el contrario, un setter es un método público que permite cambiar el valor de un atributo privado, generalmente validando que el nuevo valor sea válido antes de asignarlo.

En el ejemplo anterior de la clase `Punto`, los métodos `getX()`, `getY()`, `setX(double x)` y `setY(double y)` son ejemplos de getters y setters respectivamente. Esta aproximación proporciona un control fino sobre cómo se accede y modifica el estado del objeto: permite agregar validaciones en los setters (por ejemplo, verificar que las coordenadas no sean negativas) y, si es necesario, agregar lógica adicional en los getters (como calcular un valor en lugar de simplemente retornarlo). Aunque podría parecer más simple hacer los atributos públicos, esta práctica permite cambiar la implementación interna sin afectar la interfaz pública.


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### Respuesta


No, la "seguridad" a la que se refiere la ocultación de información no está relacionada con ataques de seguridad o hacking en el sentido de ciberseguridad. Se refiere a la "seguridad de tipos" y la "consistencia del programa": garantizar que los objetos nunca lleguen a un estado inválido o inconsistente debido a usos incorrectos o accidentes del programador. Por ejemplo, si un atributo representa un radio que debe ser siempre positivo, sin la ocultación de información, un desarrollador podría asignarlo accidentalmente a un valor negativo, rompiendo la lógica del programa.

La seguridad que proporciona la encapsulación es contra errores de programación, no contra ataques maliciosos. Un usuario con acceso al código fuente en Java pode, en teoría, usar reflexión para acceder a miembros privados, pero esto sería una violación deliberada de las restricciones de diseño. El propósito principal es comunicar la intención del diseño, establecer límites claros sobre cómo se debe usar una clase y prevenir que cambios accidentales en el código rompan las invariantes que garantizan el funcionamiento correcto del programa.


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### Respuesta


Un miembro de instancia es un atributo o método que pertenece a cada objeto (instancia) de manera individual. Cada objeto creado tiene sus propias copias de los atributos de instancia con valores potencialmente diferentes. En contraste, un miembro de clase (declarado con la palabra clave `static`) es compartido por todas las instancias de la clase: existe una sola copia para toda la clase, no una copia por objeto. Si se modifica un miembro de clase, el cambio es visible para todas las instancias.

Sí, los miembros de clase también se pueden ocultar usando los mismo modificadores `private`, `public` y otros. Un atributo de clase privado podría usarse para mantener un contador o un registro global que solo la clase puede modificar internamente. Del mismo modo, un método de clase privado podría contener lógica auxiliar que solo es utilizada internamente. La diferencia fundamental es el ámbito: los miembros de instancia varían de un objeto a otro, mientras que los miembros de clase son únicos para toda la clase y persisten mientras la clase exista cargada en memoria.


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Respuesta


Sí, los constructores privados tienen sentido en ciertos escenarios. El caso más común es en el patrón Singleton, donde se quiere garantizar que una clase solo tenga una única instancia en todo el programa. Un constructor privado previene que código externo cree nuevas instancias; en su lugar, la clase proporciona un método estático que controla la creación y retorna la instancia única. Otro caso es cuando una clase no quiere ser instanciada directamente, como una clase de utilidades que solo contiene métodos estáticos.


## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### Respuesta


Los miembros de clase en Java se indican utilizando la palabra clave `static`. Un miembro de clase es compartido por todas las instancias de la clase y se puede acceder directamente a través del nombre de la clase sin necesidad de crear un objeto. A continuación, se muestra un ejemplo de la clase `Punto` extendida con miembros de clase para rastrear los valores máximos:

```java
public class Punto {
    private double x;
    private double y;
    
    private static double maxX = Double.NEGATIVE_INFINITY;
    private static double maxY = Double.NEGATIVE_INFINITY;
    
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
        if (x > maxX) maxX = x;
        if (y > maxY) maxY = y;
    }
    
    public static double getMaxX() {
        return maxX;
    }
    
    public static double getMaxY() {
        return maxY;
    }
    
    // ... otros métodos
}
```

En este ejemplo, `maxX` y `maxY` son atributos de clase privados que mantienen un registro de los valores máximos establecidos en toda la clase. Se acceden a través de métodos de clase estáticos `getMaxX()` y `getMaxY()`. Cada vez que se crea un nuevo `Punto`, el constructor verifica y actualiza estos valores máximos globales, haciendo que todos los puntos del programa compartan esta información.


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

### Respuesta

Un método factoría es un método estático que actúa como una alternativa al constructor para crear instancias de una clase, usualmente aplicando una lógica de transformación. A continuación se presenta el método factoría solicitado:

```java
public static Punto crearPuntoRedondeado(double x, double y) {
    double xRedondeado = Math.round(x);
    double yRedondeado = Math.round(y);
    return new Punto(xRedondeado, yRedondeado);
}
```

Sí, se ha usado `static` porque este método no necesita acceso a ningún atributo de instancia específica; es una operación de clase que puede ser llamada sin necesidad de crear un objeto previamente. Se invocaría así: `Punto p = Punto.crearPuntoRedondeado(3.7, 4.2)`, lo que crearía un nuevo punto con coordenadas (4.0, 4.0). Los métodos factoría son útiles para encapsular lógica de creación compleja y proporcionar alternativas significativas a los constructores estándar.


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### Respuesta

La siguiente implementación utiliza un array interno para almacenar las coordenadas, manteniendo exactamente la misma interfaz pública:

```java
public class Punto {
    private double[] coordenadas = new double[2];
    
    public Punto(double x, double y) {
        coordenadas[0] = x;
        coordenadas[1] = y;
    }
    
    public double getX() {
        return coordenadas[0];
    }
    
    public double getY() {
        return coordenadas[1];
    }
    
    public void setX(double x) {
        coordenadas[0] = x;
    }
    
    public void setY(double y) {
        coordenadas[1] = y;
    }
    
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(coordenadas[0] * coordenadas[0] + 
                        coordenadas[1] * coordenadas[1]);
    }
}
```

Esta refactorización demuestra una de las ventajas clave de la encapsulación: la interfaz pública permanece completamente sin cambios, de modo que cualquier código que use la clase `Punto` seguirá funcionando sin modificaciones. Solo la implementación interna ha cambiado. Esto es posible porque se utilizaron métodos getters y setters en lugar de acceso directo a atributos públicos, lo que permitió cambiar cómo se almacenan los datos internamente sin afectar al usuario de la clase.


## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### Respuesta

Aunque podría parecer equivalente, mantener un atributo privado con getters y setters públicos es superior a declararlo público directamente. La razón es que los setters permiten agregar lógica de validación. En el caso de un setter trivial que simplemente asigna el valor, no hay ventaja aparente, pero en el futuro ese setter puede ser modificado para validar el nuevo valor sin cambiar la interfaz pública. Además, si el atributo fuera público, cambiar a getters y setters después sería un cambio en la interfaz que rompería el código cliente.

La convención más habitual en Java y en la mayoría de lenguajes orientados a objetos es que los atributos sean privados. Los únicos que típicamente son públicos son las constantes (atributos `static final`). Esta práctica está directamente relacionada con las invariantes de clase: al ocultar los atributos, se garantiza que solo los métodos de la clase puedan modificarlos, lo que permite mantener las restricciones necesarias para que el objeto siempre esté en un estado válido. Si cualquier parte del código pudiera modificar directamente los atributos, como en C con estructuras, sería imposible garantizar las invariantes.


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Respuesta

Una clase es inmutable cuando sus instancias no pueden cambiar de estado una vez creadas. Esto significa que no hay setters ni otros métodos que modifiquen los atributos de la clase después de la inicialización en el constructor. Un ejemplo en Java es la clase `String`: una vez creada una cadena, no se puede cambiar (aunque concatenar cadenas crea nuevas instancias). Para hacer una clase inmutable en Java, se deben declarar todos los atributos como `private final` y no proporcionar métodos que permitan modificarlos.

Un método modificador es cualquier método que cambia el estado de un objeto. Un setter es un tipo específico de método modificador, pero no todos los métodos modificadores son setters. Por ejemplo, un método `mover()` podría cambiar la posición de un objeto sin ser un setter. Las clases inmutables no tienen métodos modificadores de ningún tipo. Las ventajas de las clases inmutables incluyen: (1) simplicidad y previsibilidad, ya que el estado no cambia después de la creación; (2) seguridad en programas multihilo, porque no se requieren sincronizaciones; (3) seguridad al guardarlas o pasarlas como referencias, sin temor a que sean modificadas inesperadamente; y (4) pueden ser reutilizadas con seguridad sin hacer copias defensivas.


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### Respuesta

No, no es recomendable incluir setters automáticamente para todos los atributos privados. Los setters deben ser incluidos solo cuando tenga sentido permitir la modificación de ese atributo después de la creación del objeto. Si un atributo no debería cambiar, no debe tener un setter, aunque tenga un getter. Por ejemplo, en la clase `Punto`, podría ser válido no proporcionar setters y hacer que los puntos sean inmutables una vez creados. La decisión debe basarse en el propósito y el diseño de la clase.

Como convención general, se recomienda ser "conservador" con los setters: solo proporcionar los que realmente sean necesarios para el funcionamiento esperado de la clase. Una clase no debería permitir modificaciones innecesarias de su estado. Esto reduce la complejidad, previene cambios accidentales y facilita el mantenimiento. En algunos IDEs como Eclipse o IntelliJ IDEA, al crear una clase, se ofrece generar automáticamente getters y setters para todos los atributos, pero es responsabilidad del programador eliminar los que no sean realmente necesarios.


## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

### Respuesta

La clase `String` en Java es inmutable. Una vez creada una cadena, no puede cambiar. Cuando se concatenan dos cadenas usando el operador `+` o el método `concat()`, Java no modifica la cadena original; en su lugar, crea una nueva cadena que contiene el resultado de la concatenación. Las cadenas originales permanecen sin cambios en memoria. Esto tiene implicaciones importantes para el rendimiento: si se realiza una serie de concatenaciones, por ejemplo dentro de un bucle, cada operación crea una nueva cadena, consumiendo memoria y tiempo de procesamiento significativamente.

Para evitar este problema cuando se necesita construir paso a paso una cadena muy larga, se debe utilizar la clase `StringBuilder` (o `StringBuffer` en aplicaciones multihilo). `StringBuilder` es mutable y acumula los cambios internamente de manera eficiente, agregando nuevas partes sin crear nuevos objetos cada vez. Solo al final, cuando se llama a `toString()`, se crea la cadena resultante final. Por ejemplo: `StringBuilder sb = new StringBuilder(); sb.append("hola"); sb.append(" "); sb.append("mundo");` es mucho más eficiente que realizar tres concatenaciones con el operador `+`. Esta es una optimización común y recomendada cuando se trabaja con muchas operaciones de cadenas.


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

### Respuesta

En POO, existen dos formas de comparar objetos: por identidad (¿son el mismo objeto en memoria?) o por contenido (¿tienen los mismos valores en sus atributos?). En Java, el operador `==` compara por identidad, verificando si dos referencias apuntan al mismo objeto en memoria. Para comparar por contenido, se usa el método `equals()`. Por defecto, la implementación de `equals()` heredada del método `Object` compara por identidad (funciona como `==`), así que diferentes métodos deben sobrescribirla si desean una comparación basada en el contenido.

El método `equals()` debe ser sobrescrito en una clase cuando tiene sentido comparar dos instancias por su contenido. Por ejemplo, para la clase `Punto`, uno podría querer que dos puntos con las mismas coordenadas se consideren iguales. Las cadenas de texto en Java deben compararse siempre usando `equals()` o `equalsIgnoreCase()`, nunca con `==`, porque `==` solo verifica si son el mismo objeto en memoria, no si contienen el mismo texto. Por ejemplo: `"hola".equals("hola")` devuelve `true`, pero `new String("hola") == "hola"` devuelve `false` porque crea objetos diferentes en memoria, aunque contengan el mismo texto.


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers?

### Respuesta

Las clases wrapper (envolventes) son clases que envuelven tipos de datos primitivos en objetos. Java tiene tipos primitivos (como `int`, `double`, `boolean`) que no son objetos y que tienen limitaciones: no pueden ser `null`, no pueden almacenarse en colecciones que requieren objetos, y no tienen métodos. Las clases wrapper correspondientes son `Integer`, `Double`, `Boolean`, etc., que permiten utilizar estos tipos primitivos como objetos. Por ejemplo, `Integer` es una clase que envuelve un valor `int`.

En Java, la conversión entre primitivos y sus wrappers es parcialmente automática gracias a características llamadas "autoboxing" (convertir primitivo a wrapper) y "unboxing" (convertir wrapper a primitivo). El programador puede escribir `Integer x = 5;` y Java automáticamente crea un objeto `Integer` que contiene el valor primitivo 5. Las ventajas de las clases wrapper incluyen: permitir usar primitivos donde se requieren objetos, proporcionar métodos útiles (como conversiones de cadenas), y permitir valores `null`. No todos los lenguajes orientados a objetos tienen este problema: lenguajes como Python, Ruby o Smalltalk tratan todo como objetos desde el principio, incluyendo números y booleanos, por lo que no necesitan clases wrapper.


## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### Respuesta

Un tipo de dato enumerado (enum) es un tipo que define un conjunto fijo y predeterminado de valores posibles. Por ejemplo, un enum que represente los días de la semana tendría exactamente siete valores posibles: Lunes, Martes, Miércoles, etc. En lugar de usar números o cadenas para representar estos conceptos (lo cual es propenso a errores), un enum proporciona un conjunto controlado de opciones válidas. En Java, un tipo enumerado es efectivamente una clase especial que hereda de la clase `Enum`, aunque el usuario la declara usando la palabra clave `enum`.

En términos de encapsulación, los enumerados en Java ofrecen ventajas significativas. Primero, garantizan que una variable enumerada solo puede tener uno de los valores predefinidos, eliminando la posibilidad de estados inválidos (a diferencia de usar un `String` donde se podría pasar "Lun" por error). Segundo, los enums pueden tener atributos privados y métodos privados para encapsular lógica asociada con cada constante. Tercero, no se pueden crear nuevas instancias de un enum desde fuera; las únicas instancias permitidas son las predefinidas. Esto proporciona un control total sobre qué valores existen y cómo se comportan, mejorando la seguridad y la claridad del código.


## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado. Añade además cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### Respuesta

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
    
    Mes(int dias, int ordinal) {
        this.dias = dias;
        this.ordinal = ordinal;
    }
    
    public int getDias() {
        return dias;
    }
    
    public int getOrdinal() {
        return ordinal;
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

Este enum `Mes` demuestra la potencia de los enumerados para encapsular datos y comportamiento. Cada constante de enum recibe dos parámetros en su constructor privado: el número de días que tiene y su ordinal en el año. Los métodos privados del constructor garantizan que solo las doce instancias predefinidas existan y que sean inmutables. Los métodos para detectar estaciones permiten consultar información compleja sobre cada mes de manera orientada a objetos, considerando el hemisferio. Así, el cliente del enum solo necesita llamar a `Mes.MARZO.esDePrimavera(true)` para saber si marzo es primavera en el hemisferio norte, sin necesidad de conocer los detalles internos de cómo se determina esto.
