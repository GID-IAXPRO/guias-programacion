<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Clases y Objetos". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: ninguno.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->

# TEMA 1. Clases y objetos

## 1. ¿Cuáles son las cuatro características básicas de la programación orientada a objetos? Describe brevemente cada una

### 1. Abstracción

La abstracción consiste en identificar las características esenciales de un objeto del mundo real, descartando los detalles que no son relevantes para el contexto del programa. En lugar de manejar variables sueltas como se haría en C (por ejemplo, `float x, y;`), se define un concepto superior, como una clase `Punto`, que representa esa entidad de forma simplificada.

Este proceso permite centrarse en el "qué" hace un objeto en lugar de en el "cómo" está implementado internamente. Se crean modelos que representan la realidad de manera lógica, facilitando la gestión de la complejidad al trabajar con representaciones mentales más claras y menos dependientes del bajo nivel.

### 2. Encapsulamiento

El encapsulamiento es el mecanismo que agrupa los datos (atributos) y el código (métodos) en una única unidad o clase, restringiendo el acceso directo a los mismos desde el exterior. A diferencia de las `struct` tradicionales de C donde cualquier parte del programa puede modificar un campo, aquí se utilizan modificadores de acceso para proteger la integridad del objeto.

Mediante esta característica, se oculta el estado interno del objeto y solo se permite su modificación a través de una interfaz controlada (métodos públicos). Esto evita efectos secundarios no deseados y garantiza que los datos solo cambien bajo las reglas definidas por el propio programador dentro de la clase.

### 3. Herencia

La herencia permite la creación de nuevas clases basadas en clases ya existentes, estableciendo una jerarquía de "es un". Una clase derivada hereda automáticamente los atributos y comportamientos de su clase base, lo que promueve significativamente la reutilización del código y evita la duplicidad de lógica.

En términos prácticos, si se dispone de una clase `Vehiculo`, se pueden crear subclases como `Coche` o `Moto` que compartan la estructura común pero añadan sus propias particularidades. Esto facilita el mantenimiento, ya que cualquier cambio en la lógica general de la clase base se refleja automáticamente en todas sus descendientes.

### 4. Polimorfismo

El polimorfismo es la capacidad que permite que diferentes clases respondan de manera distinta a un mismo mensaje o llamada a un método. Aunque varios objetos compartan una misma interfaz o nombre de función, la ejecución concreta dependerá del tipo de objeto que la invoque en tiempo de ejecución.

Esta característica otorga una gran flexibilidad al sistema, permitiendo escribir código genérico que puede interactuar con una amplia variedad de objetos sin conocer su tipo exacto de antemano. Es el pilar que permite extender las funcionalidades del software de manera sencilla, añadiendo nuevos tipos de objetos sin necesidad de modificar el código que ya los utiliza.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

Para dar respuesta a esta cuestión, es importante destacar que la mayoría de los lenguajes modernos han adoptado la Programación Orientada a Objetos (POO) debido a su capacidad para organizar sistemas complejos. Aunque muchos de ellos permiten otros estilos de programación, su diseño principal está optimizado para trabajar con clases y objetos.

A continuación, se describen cuatro de los lenguajes más influyentes y utilizados en la actualidad que implementan este paradigma:

---

### Java

Java es, probablemente, el lenguaje más representativo de la POO. Fue diseñado bajo la premisa de "escribir una vez, ejecutar en cualquier lugar", lo que se logra mediante la Máquina Virtual de Java (JVM). A diferencia de C++, en Java casi todo debe residir dentro de una clase, lo que obliga al programador a seguir los principios de orientación a objetos desde el primer momento.

Es ampliamente utilizado en el desarrollo de aplicaciones empresariales de gran escala y en el ecosistema de Android. Su sintaxis resultará familiar para quien provenga de C/C++, pero elimina la gestión manual de memoria (punteros y `free()`) gracias al uso de un "recolector de basura" (*Garbage Collector*), lo que reduce errores comunes de segmentación.

### C++

C++ se define como un lenguaje multiparadigma que extiende el lenguaje C original añadiendo capacidades de orientación a objetos. Al ser una evolución directa de C, permite mantener un control de bajo nivel sobre el hardware y la memoria, lo que lo hace ideal para el desarrollo de sistemas donde el rendimiento es crítico, como motores de videojuegos, navegadores web o software de edición de vídeo.

Una de sus características más potentes es que permite combinar la programación estructurada tradicional con la POO. Esto ofrece una gran versatilidad, permitiendo al desarrollador decidir cuándo utilizar clases y objetos y cuándo optar por funciones procedimentales puras, manteniendo siempre una compatibilidad casi total con el código escrito en C.

### Python

Python es un lenguaje de alto nivel conocido por su sintaxis clara y legible, que se asemeja al lenguaje humano. Aunque se utiliza mucho para scripts sencillos, es un lenguaje orientado a objetos desde su núcleo: en Python, prácticamente todo (incluyendo números y cadenas de texto) es un objeto con sus propios atributos y métodos.

Su popularidad ha crecido de forma exponencial en campos como la ciencia de datos, la inteligencia artificial y el desarrollo web. Ofrece una implementación de la POO muy flexible y menos rígida que la de Java, permitiendo, por ejemplo, la herencia múltiple de una manera más directa que otros lenguajes modernos.

### C# (C-Sharp)

Desarrollado por Microsoft, C# es un lenguaje orientado a objetos creado para competir directamente con Java en el entorno de sistemas Windows y aplicaciones de escritorio. Al igual que Java, utiliza un entorno de ejecución intermedio (el .NET Framework) y gestiona la memoria de forma automática, facilitando un desarrollo seguro y rápido.

En la actualidad, su uso se ha expandido enormemente gracias al motor de videojuegos Unity, donde es el lenguaje principal. Presenta una sintaxis muy elegante que ha sabido recoger las mejores características de C++ y Java, añadiendo funcionalidades modernas que simplifican tareas como el manejo de eventos o las consultas a bases de datos.


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

Entendido, ajustaré la extensión para ser más directo. Si con dos o tres párrafos queda claro el concepto, lo dejaré ahí para no rellenar innecesariamente.

Aquí tienes la respuesta a la tercera pregunta:

---

## 3. Los paradigmas anteriores a la POO, ¿Qué es la programación estructurada? y, todavía mejor, ¿Qué es la programación modular?

### Programación Estructurada

La programación estructurada es un paradigma que organiza el código de manera lineal y lógica, utilizando exclusivamente tres estructuras de control: secuencia, selección (`if`, `switch`) e iteración (`for`, `while`). Este enfoque surgió para eliminar el uso de saltos desordenados (como el `goto`), que hacían que el flujo del programa fuera difícil de seguir y mantener, un fenómeno conocido como "código espagueti".

En este modelo, el programa se percibe como una serie de pasos que se ejecutan de arriba hacia abajo. El énfasis se pone en la lógica del algoritmo y en el control del flujo, asegurando que cada bloque de código tenga un único punto de entrada y un único punto de salida, lo que facilita enormemente la comprensión del programa y la detección de errores.

### Programación Modular

La programación modular da un paso más allá al consistir en la fragmentación de un programa en partes más pequeñas y relativamente independientes llamadas módulos. Cada módulo agrupa un conjunto de funciones y datos relacionados que realizan una tarea específica. En el contexto de C, esto se visualiza claramente al separar el código en diferentes archivos `.c` y sus respectivos encabezados `.h`.

Este enfoque permite aplicar el principio de "divide y vencerás", facilitando que diferentes programadores trabajen en distintas partes del sistema simultáneamente sin interferir entre sí. Además, mejora la legibilidad y permite la reutilización de módulos enteros en otros proyectos, reduciendo el tiempo de desarrollo y simplificando las pruebas unitarias.


## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

Para definir un objeto dentro de este paradigma, es necesario identificar tres componentes fundamentales que lo distinguen de una simple variable o estructura de datos tradicional. Estos elementos permiten que el objeto sea una entidad autónoma con identidad propia.

A continuación se describen los tres elementos:

### 1. Estado (Atributos)

El estado de un objeto está compuesto por los datos o características que lo definen en un momento determinado. En programación, estos se representan mediante **variables** o campos (atributos) que almacenan valores específicos. Por ejemplo, en un objeto de la clase `Coche`, su estado podría incluir el color, la marca y la velocidad actual.

Es importante destacar que el estado puede ser dinámico; los valores de los atributos pueden cambiar a lo largo de la ejecución del programa como resultado de las interacciones, pero la estructura de los datos que los contienen permanece definida por la clase.

### 2. Comportamiento (Métodos)

El comportamiento define las acciones que un objeto puede realizar o las operaciones que se pueden ejecutar sobre él. Esto se implementa mediante **funciones** internas denominadas métodos. Siguiendo el ejemplo del `Coche`, su comportamiento incluiría acciones como `acelerar()`, `frenar()` o `girar()`.

El comportamiento suele estar estrechamente ligado al estado, ya que un método puede consultar o modificar los atributos del objeto. Por ejemplo, el método `acelerar()` modificará el atributo `velocidad`, alterando así el estado interno de la entidad.

### 3. Identidad

La identidad es la propiedad que permite diferenciar a un objeto de todos los demás, incluso si tienen exactamente el mismo estado (mismos atributos con mismos valores). En la memoria del ordenador, la identidad se corresponde generalmente con la **dirección de memoria** única donde reside el objeto.

Gracias a la identidad, el sistema puede distinguir entre dos instancias distintas. Por ejemplo, aunque existan dos objetos `Coche` con la misma marca, modelo y color, cada uno es una entidad independiente; si uno de ellos choca, el estado del otro permanece intacto, ya que poseen identidades diferentes.


## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

Para entender la POO es fundamental distinguir entre el molde y el producto final. A continuación, se explican estos conceptos y su relación:

### Definición de Clase e Instancia

Una **clase** es una plantilla o molde abstracto que define la estructura y el comportamiento que tendrán los objetos creados a partir de ella. En términos de C, se puede comparar con un prototipo o una definición de `struct` avanzada que, además de datos, incluye las funciones que los manipulan. La clase no ocupa espacio en memoria para datos específicos, sino que simplemente establece qué atributos y métodos existirán.

Una **instancia** es, precisamente, la materialización de esa clase en la memoria del ordenador. El proceso de crear una instancia se conoce como **instanciación**. Cuando se instancia una clase, se reserva espacio físico para almacenar los valores concretos de sus atributos, convirtiendo el diseño abstracto de la clase en un ente real y operativo dentro del programa.

### Clase vs. Objeto

No son lo mismo: la diferencia es de concepto y existencia. Mientras que la clase es el concepto genérico (como el plano de una casa), el **objeto** es la realización física (la casa construida). Se pueden crear múltiples objetos a partir de una sola clase, y cada uno de ellos tendrá su propia identidad y estado independiente, aunque todos compartan la misma estructura definida por el molde original.

### El concepto de clase en los lenguajes POO

Aunque la mayoría de los lenguajes populares (como Java, C++ o C#) se basan en clases, **no todos los lenguajes orientados a objetos las manejan**. Existe una variante denominada **POO basada en prototipos**, donde no existen las clases como moldes previos. En estos lenguajes, los objetos se crean clonando otros objetos ya existentes (prototipos) y añadiéndoles nuevas características sobre la marcha.

El ejemplo más famoso de este último tipo es **JavaScript**. En este modelo, la estructura de un objeto es mucho más flexible, ya que puede evolucionar durante la ejecución del programa sin depender de una definición estática cerrada como ocurre en los lenguajes basados en clases tradicionales.


## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

La gestión de la memoria es uno de los puntos donde más se nota el cambio al pasar de C a lenguajes de alto nivel como Java. A continuación, se detalla cómo se gestionan estas entidades:

### Almacenamiento en memoria: Stack vs. Heap

En la mayoría de los lenguajes, los objetos se almacenan en una zona de memoria dinámica llamada **Heap** (montículo). A diferencia del **Stack** (pila), que se usa para variables locales y llamadas a funciones con un tamaño fijo y vida corta, el Heap es un espacio mucho más grande y flexible donde los objetos pueden residir durante el tiempo que sea necesario, independientemente de la función que los creó.

Lo que se guarda habitualmente en el Stack es únicamente la **referencia** (o puntero) al objeto, no el objeto en sí. Por ejemplo, al declarar un objeto en Java, la variable local en el Stack actúa como una "dirección" que apunta hacia los datos reales del objeto que están alojados en el Heap.

### Variaciones entre lenguajes

Este comportamiento **no es igual en todos los lenguajes**. En C++, el programador tiene la libertad de elegir: puede crear un objeto en el Stack (comportándose como una variable local de C) o en el Heap usando el operador `new`. Sin embargo, en lenguajes como Java o C#, existe una separación más estricta: los tipos primitivos (como `int` o `boolean`) suelen ir al Stack, mientras que todos los objetos sin excepción se alojan en el Heap.

Esta diferencia es crucial para el rendimiento y la gestión de recursos. Mientras que el acceso al Stack es extremadamente rápido y automático, el Heap requiere una gestión más compleja para encontrar espacio libre y, sobre todo, para liberar la memoria una vez que el objeto ya no es necesario.

### La Recolección de Basura (Garbage Collection)

La **recolección de basura** es un proceso automático encargado de gestionar la memoria del Heap. Su función principal es identificar qué objetos ya no tienen ninguna referencia apuntando a ellos (es decir, que ya no pueden ser alcanzados por el programa) y liberar ese espacio de forma automática.

A diferencia de C, donde el programador debe recordar usar `free()` para evitar fugas de memoria (*memory leaks*), en lenguajes con Recolector de Basura (como Java o Python) el sistema asume esa responsabilidad. Esto aumenta la seguridad y fiabilidad del software, ya que evita errores comunes como intentar acceder a memoria ya liberada o el agotamiento de la memoria por olvidos en la liberación de recursos.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

En la Programación Orientada a Objetos, las funciones dejan de ser entes aislados para convertirse en parte integral de las entidades. A continuación se explican estos conceptos:

### Definición de Método

Un **método** es una función que se define dentro de una clase y que opera sobre los datos (atributos) de los objetos de esa clase. Representa el comportamiento de un objeto; es decir, aquello que el objeto "sabe hacer". A diferencia de las funciones en C, un método siempre tiene acceso implícito a los datos del objeto que lo invoca, lo que permite una comunicación directa entre el comportamiento y el estado sin necesidad de pasar todas las variables como argumentos.

Cada método tiene una firma que incluye su nombre, el tipo de dato que devuelve y su lista de parámetros. En Java, se utilizan para implementar la interfaz del objeto, permitiendo que el mundo exterior interactúe con él de manera controlada y segura, respetando el principio de encapsulamiento.

### Sobrecarga de Métodos

La **sobrecarga de métodos** es la capacidad de definir en una misma clase varios métodos con el mismo nombre, pero con diferentes listas de parámetros (ya sea en cantidad o en tipo de datos). Para que el compilador pueda distinguirlos, la firma de cada método debe ser única. Por ejemplo, se puede tener un método `dibujar(int radio)` y otro `dibujar(int ancho, int alto)` dentro de la misma clase.

Esta característica mejora la legibilidad y la usabilidad del código, ya que permite realizar operaciones conceptualmente similares con diferentes tipos de entrada sin tener que inventar nombres distintos (como `dibujarCirculo` o `dibujarRectangulo`). Es el compilador quien, en tiempo de compilación, decide qué versión del método ejecutar basándose en los argumentos que se le pasan en la llamada.


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

Para seguir el estándar de Java, la clase se define en un archivo con su mismo nombre. A diferencia de C, no se requiere separar la declaración en un `.h` y la implementación en un `.c`; todo se escribe dentro del bloque de la clase.

A continuación, se presenta el código solicitado siguiendo una estructura mínima:

### Definición de la clase `Punto`

```java
public class Punto {
    // Atributos con visibilidad por defecto (package-private)
    double x;
    double y;

    // Método para calcular la distancia al origen (0,0)
    public double calculaDistanciaAOrigen() {
        // Se utiliza el teorema de Pitágoras: raíz cuadrada de (x^2 + y^2)
        return Math.sqrt(x * x + y * y);
    }
}

```

### Ejemplo de uso (Instanciación)

Para utilizar la clase, es necesario crear una instancia mediante el operador `new` dentro de un método principal (`main`).

```java
public class Principal {
    public static void main(String[] args) {
        // 1. Creación de la instancia (Objeto)
        Punto miPunto = new Punto();

        // 2. Asignación de valores a los atributos
        miPunto.x = 3.0;
        miPunto.y = 4.0;

        // 3. Llamada al método y obtención del resultado
        double distancia = miPunto.calculaDistanciaAOrigen();

        System.out.println("La distancia al origen es: " + distancia);
    }
}



### Análisis del código para un programador de C

En este ejemplo se pueden observar varios conceptos clave que difieren de la programación estructurada tradicional:

* **Agrupación de datos y lógica:** A diferencia de una `struct` de C, la clase `Punto` contiene tanto las variables (`x`, `y`) como la función que opera sobre ellas (`calculaDistanciaAOrigen`). No es necesario pasar el objeto como argumento al método, ya que este tiene acceso interno a sus propios atributos.
* **Gestión de memoria:** Al ejecutar `new Punto()`, Java reserva automáticamente espacio en el **Heap** para el objeto. La variable `miPunto` es, en realidad, una referencia (similar a un puntero en C) que apunta a esa zona de memoria, pero sin la necesidad de gestionar manualmente su liberación.
* **Acceso a miembros:** Se utiliza el operador punto (`.`) tanto para acceder a las variables de estado como para invocar el comportamiento del objeto. Esto mantiene una sintaxis limpia y coherente con lo que se espera de una entidad autónoma.


## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

Para un programador acostumbrado a C, el concepto de "punto de entrada" en Java resultará familiar, aunque su implementación está estrictamente ligada a la estructura de clases.

### El punto de entrada en Java

Al igual que en C o C++, el punto de entrada es el método **`main`**. Sin embargo, en Java este método debe cumplir con una firma muy específica: `public static void main(String[] args)`. Debe ser público para que la Máquina Virtual de Java (JVM) pueda acceder a él, y debe estar contenido obligatoriamente dentro de una clase.

A diferencia de C, donde el `main` existe de forma global, en Java el programa comienza su ejecución llamando al método `main` de la clase que se le indique a la JVM. Si un proyecto tiene varias clases y cada una tiene su propio método `main`, el programador debe especificar cuál de ellas debe actuar como punto de partida.

### El modificador `static`

El término **`static`** indica que un miembro (método o atributo) pertenece a la **clase en sí** y no a una instancia (objeto) concreta. Esto significa que se puede invocar el método o acceder al atributo sin necesidad de crear un objeto con `new`. Por esta razón el `main` es estático: la JVM necesita poder arrancarlo antes de que existan objetos en memoria.

No se emplea solo para el `main`. Los atributos estáticos son útiles para compartir información entre todas las instancias de una clase (como un contador de objetos creados), mientras que los métodos estáticos suelen usarse para utilidades o funciones matemáticas (como `Math.sqrt()` en Java), donde no se requiere el estado de un objeto específico para realizar el cálculo.

### Combinación de `static` y `final`

Cuando se combinan `static` y **`final`**, se está definiendo una **constante de clase**. El modificador `final` en Java equivale a impedir que un valor sea modificado una vez asignado (similar a `const` en C). Al sumarle `static`, la constante es compartida por todos los objetos y reside en un único lugar de la memoria de la clase.

Esta combinación es el estándar en Java para definir valores fijos globales, como `Math.PI`. Al ser `static`, se accede a ella como `NombreClase.CONSTANTE`, y al ser `final`, el compilador garantiza que ningún proceso pueda alterar ese valor durante la ejecución del programa, proporcionando seguridad y claridad al código.


## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

Para un programador que viene de C, el proceso de ejecución en Java presenta un paso intermedio fundamental que lo diferencia del binario nativo que genera `gcc`.

### Compilación y ejecución en línea de comandos

Para poner en marcha un programa, se utilizan dos herramientas principales del JDK (Java Development Kit). Primero, se utiliza **`javac`** seguido del nombre del archivo fuente (por ejemplo, `javac Punto.java`). Este comando no genera un ejecutable directo (como un `.exe` o un `a.out`), sino que produce un archivo con extensión **`.class`**.

Una vez generado el archivo `.class`, se utiliza el comando **`java`** seguido únicamente del nombre de la clase (sin la extensión), por ejemplo: `java Principal`. Este segundo paso es el que realmente inicia la ejecución, cargando el programa en el entorno de Java para que empiece a funcionar.

### ¿Java es compilado? El Byte-code y los archivos `.class`

La respuesta corta es que Java es **ambas cosas**: compilado e interpretado. El archivo `.class` que mencionamos anteriormente contiene el **byte-code**, que es un lenguaje de bajo nivel intermedio. No es código máquina que el procesador entienda directamente, sino un conjunto de instrucciones optimizadas para ser ejecutadas por un software específico.

Esta estrategia permite la portabilidad: el programador compila su código una sola vez a *byte-code* y ese mismo archivo `.class` puede funcionar en cualquier sistema operativo (Windows, Linux, macOS) sin necesidad de ser recompilado, siempre que dicho sistema cuente con el entorno de Java adecuado.

### La Máquina Virtual de Java (JVM)

La **Máquina Virtual de Java (JVM)** es el corazón de este ecosistema. Se trata de un software que actúa como una capa de abstracción entre el *byte-code* y el hardware real. Su función es "interpretar" el *byte-code* y traducirlo a instrucciones que el procesador de la máquina local pueda ejecutar en tiempo real.

Además de la ejecución, la JVM se encarga de tareas críticas que en C gestiona el programador o el sistema operativo, como la gestión de hilos, la verificación de seguridad del código y, especialmente, la **recolección de basura**. Es, en esencia, el "ordenador imaginario" sobre el cual corren todos los programas Java, garantizando que se comporten igual independientemente de la máquina física que haya debajo.


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

Para completar la visión técnica de cómo nacen los objetos, es fundamental entender el proceso de inicialización y el papel del operador `new`.

### El operador `new`

En Java, el operador **`new`** es el encargado de solicitar memoria dinámica en el **Heap** para crear una nueva instancia de una clase. Su funcionamiento es análogo a la combinación de `malloc()` y la definición de una estructura en C, pero con una diferencia clave: `new` no solo reserva el espacio físico, sino que también invoca automáticamente al **constructor** de la clase para inicializar el objeto.

Cuando se ejecuta una instrucción como `Punto p = new Punto();`, el operador `new` devuelve la dirección de memoria (referencia) donde se ha creado el objeto, la cual se almacena en la variable `p`. Sin este operador, la variable sería simplemente una referencia vacía (`null`) que no apunta a ninguna entidad real.

### El Constructor

Un **constructor** es un método especial que se ejecuta única y exclusivamente en el momento de la creación de un objeto. Su función principal es asegurar que el objeto nazca con un estado válido, asignando valores iniciales a sus atributos. En Java, el constructor se identifica porque tiene el mismo nombre que la clase y **no especifica ningún tipo de retorno** (ni siquiera `void`).

Si el programador no define ningún constructor, Java crea uno por defecto sin parámetros. Sin embargo, lo habitual es definir constructores personalizados para obligar a que, al crear un objeto, se proporcionen los datos mínimos necesarios para su existencia.

### Ejemplo en la clase `Empleado`

A continuación se presenta una clase con un constructor que inicializa los datos de un empleado. Nótese el uso de la palabra clave `this`, que se emplea para diferenciar los atributos de la clase de los parámetros que recibe el constructor (muy útil cuando tienen el mismo nombre).

```java
public class Empleado {
    // Atributos
    String dni;
    String nombre;
    String apellidos;

    // Constructor: recibe los datos y los asigna al objeto
    public Empleado(String dni, String nombre, String apellidos) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellidos = apellidos;
    }
}

// Ejemplo de uso
public class Prueba {
    public static void main(String[] args) {
        // Al usar 'new', estamos obligados a pasar los datos que pide el constructor
        Empleado emp = new Empleado("12345678X", "Juan", "Pérez García");
    }
}

```

Este enfoque garantiza que no pueda existir un objeto `Empleado` en el sistema que no tenga, al menos, un DNI y un nombre asignados desde el primer microsegundo de su vida.

---

## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

Para un programador de C, la referencia **`this`** puede entenderse como un puntero implícito que el sistema maneja por nosotros. A continuación, se detalla su funcionamiento y utilidad:

### Definición de `this`

La referencia **`this`** es una variable especial que existe dentro de cualquier método o constructor de una clase y que apunta directamente al **objeto actual** que está ejecutando dicho código. Es la forma que tiene un objeto de referirse a sí mismo. Cuando se accede a un atributo o se llama a otro método dentro de la clase, Java utiliza `this` de forma transparente, aunque a menudo su escritura es opcional.

Su uso principal es resolver ambigüedades entre los atributos de la clase y los parámetros de un método. Si un parámetro tiene el mismo nombre que un atributo, el nombre por sí solo hará referencia al parámetro (por una regla de cercanía o *shadowing*); para acceder al atributo de la instancia, es obligatorio anteponer `this.`.

### Diferencias entre lenguajes

Aunque el concepto es universal en la Programación Orientada a Objetos, el nombre varía según el lenguaje. En lenguajes como **C++, Java, C# y JavaScript**, se utiliza la palabra reservada `this`. Sin embargo, en otros lenguajes populares como **Python** o **PHP**, se utiliza el término **`self`** (aunque en Python es un parámetro que debe declararse explícitamente en cada método, a diferencia de Java donde es implícito).

### Ejemplo de uso en la clase `Punto`

En este ejemplo, se utiliza `this` en el constructor para distinguir las coordenadas que recibe la función de las variables propias de la clase:

```java
public class Punto {
    double x;
    double y;

    // Uso de this para evitar la ambigüedad de nombres
    public Punto(double x, double y) {
        this.x = x; // El atributo 'x' de la clase recibe el valor del parámetro 'x'
        this.y = y; // El atributo 'y' de la clase recibe el valor del parámetro 'y'
    }

    public void setUbicacion(double x, double y) {
        this.x = x;
        this.y = y;
    }
}

```

Sin el uso de `this`, una instrucción como `x = x;` dentro del constructor no tendría efecto sobre el atributo de la clase, ya que el compilador interpretaría que se está asignando el valor del parámetro a sí mismo.

---
## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

Para calcular la distancia entre dos puntos en un plano bidimensional, se aplica el teorema de Pitágoras sobre la diferencia de sus coordenadas. En este caso, el método comparará los atributos del objeto actual (representados por `this`) con los atributos del objeto pasado como argumento.

A continuación, se detalla la implementación y la lógica de este método:

### Implementación del método `distanciaA`

El método recibe una referencia a otro objeto de la misma clase `Punto`. Al estar dentro de la clase, el código tiene permiso para acceder a los atributos del parámetro `otroPunto` (incluso si fueran privados, aunque aquí tienen visibilidad por defecto).

```java
public class Punto {
    double x;
    double y;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Método que calcula la distancia entre el objeto actual y otro punto
    public double distanciaA(Punto otroPunto) {
        double diferenciaX = this.x - otroPunto.x;
        double diferenciaY = this.y - otroPunto.y;
        
        // Aplicación del teorema de Pitágoras
        return Math.sqrt(diferenciaX * diferenciaX + diferenciaY * diferenciaY);
    }
}

```

### Análisis de la lógica

En este diseño, se observa cómo interactúan dos instancias de la misma clase. Mientras que `this.x` y `this.y` representan las coordenadas de la instancia que "llama" al método, `otroPunto.x` y `otroPunto.y` representan el estado de la instancia que se envía como dato. Esta es una muestra clara de cómo los objetos pueden colaborar entre sí para resolver problemas complejos.

Desde el punto de vista de la memoria, el método `distanciaA` maneja dos referencias. En una arquitectura de C, esto equivaldría a pasar dos punteros a una función, pero en Java, la sintaxis `objeto1.distanciaA(objeto2)` deja claro que la operación es una responsabilidad del primer punto, utilizando al segundo como referencia para el cálculo.

### Ejemplo de uso

Para ejecutar este código, se instanciarían dos objetos y se invocaría el método desde cualquiera de ellos:

```java
public class Principal {
    public static void main(String[] args) {
        Punto p1 = new Punto(0, 0);
        Punto p2 = new Punto(3, 4);

        // Se calcula la distancia desde p1 hacia p2
        double resultado = p1.distanciaA(p2);

        System.out.println("La distancia entre los puntos es: " + resultado);
    }
}


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

Esta es una de las cuestiones más importantes para un programador de C/C++, ya que Java maneja los tipos de datos de forma distinta según su naturaleza. La respuesta corta es que **Java siempre pasa todo por valor**, pero el "valor" de un objeto es su **referencia**.

A continuación se detalla el comportamiento según el tipo de dato:

### El paso de objetos (como `Punto`)

Cuando se pasa un objeto como parámetro, lo que se recibe en el método es una **copia de la referencia** (el puntero, en términos de C). Al ser una copia de la dirección de memoria, tanto la variable original fuera del método como el parámetro dentro del método apuntan al **mismo objeto físico** en el Heap.

Por lo tanto, si se modifica un atributo del objeto dentro del método (por ejemplo, `otroPunto.x = 10;`), los cambios **sí afectan** al objeto fuera del método, ya que solo existe una instancia en memoria. Sin embargo, si dentro del método se intenta reasignar la variable (`otroPunto = new Punto();`), eso no afectará a la variable original, porque solo se está cambiando la copia local de la referencia.

### El paso de tipos primitivos (como `int`)

En el caso de los tipos primitivos (`int`, `double`, `boolean`, etc.), el comportamiento es idéntico al paso por valor estándar de C. El método recibe una **copia exacta del valor** numérico. Cualquier modificación que se realice sobre esa variable dentro del método es totalmente local y no tiene ninguna repercusión en la variable original fuera de la función.

Esta distinción es clave: los tipos primitivos se almacenan directamente en el **Stack**, mientras que los objetos viven en el **Heap** y se acceden mediante referencias. Por ello, el "valor" que se copia en un `int` es el número, mientras que el "valor" que se copia en un `Punto` es la dirección de memoria.

### Comparativa técnica

Para un programador de C, la analogía sería la siguiente:

* Pasar un **`int`** en Java es como pasar un `int` en C.
* Pasar un **objeto** en Java es como pasar un **puntero** (`Punto*`) por valor en C.

---
## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

En Java, el método `toString()` es una función especial que pertenece a la clase `Object` (la clase de la que heredan todas las demás). Su propósito es devolver una **representación en forma de cadena de texto** de un objeto, facilitando así su depuración y visualización.

A continuación, se explica su funcionamiento y se presenta un ejemplo práctico:

### Definición y propósito de `toString()`

Por defecto, si no se define este método, al intentar imprimir un objeto (por ejemplo, con `System.out.println(miPunto)`), Java muestra una cadena poco útil compuesta por el nombre de la clase y una dirección de memoria. Al **sobrescribir** este método, el programador define exactamente qué información del objeto se debe mostrar, transformando el estado interno (los atributos) en un formato legible.

Este concepto existe en casi todos los lenguajes modernos. En **Python** se utiliza el método especial `__str__` o `__repr__`, en **JavaScript** el método `toString()`, y en **C#** también existe el método `ToString()`. En todos los casos, el objetivo es el mismo: permitir que el objeto se "auto-describa" cuando se necesite convertirlo a texto.

### Ejemplo de `toString()` en la clase `Punto`

Para implementar este método, se debe usar la anotación `@Override`, la cual indica al compilador que estamos reemplazando la versión por defecto de la clase base.

```java
public class Punto {
    double x;
    double y;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    @Override
    public String toString() {
        // Devolvemos las coordenadas en un formato legible, por ejemplo (x, y)
        return "(" + this.x + ", " + this.y + ")";
    }
}

```

### Ejemplo de uso

Una de las mayores ventajas es que Java invoca este método automáticamente cuando se concatena un objeto con una cadena de texto o se envía a la consola.

```java
public class Principal {
    public static void main(String[] args) {
        Punto p = new Punto(5.0, 12.0);
        
        // No es necesario llamar a p.toString(); Java lo hace por nosotros
        System.out.println("La ubicación del punto es: " + p); 
        // Salida: La ubicación del punto es: (5.0, 12.0)
    }
}

## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


Esta es una reflexión excelente para alguien con tu base técnica. La respuesta corta es que una `struct` de C es el antepasado directo de una clase, pero le faltan componentes críticos para alcanzar la autonomía que define a la Programación Orientada a Objetos.

A continuación, se analizan las diferencias fundamentales:

### La `struct` como contenedor de datos vs. la Clase como entidad

En C, una `struct` es puramente un **contenedor de datos pasivo**. Es una forma de agrupar variables relacionadas en un bloque de memoria contiguo, pero la lógica que manipula esos datos reside fuera, en funciones globales. Para que una `struct` sea como una clase, le falta la capacidad de **contener comportamiento**. En una clase, los métodos están "dentro" de la entidad, lo que permite que el objeto sea responsable de sus propias acciones, garantizando que nadie modifique sus datos internos de forma incoherente.

### La falta de Encapsulamiento y Control de Acceso

A una `struct` de C le falta el **encapsulamiento**. En C, si tienes acceso a la estructura, tienes acceso a todos sus miembros; no hay forma de declarar un campo como "privado". En una clase, se pueden ocultar los detalles internos. Sin este control, las variables de una `struct` no pueden considerarse "instancias" en el sentido estricto, ya que no son cajas negras protegidas, sino simples agrupaciones de memoria expuestas a cualquier función del programa.

### El proceso de "nacimiento" y "muerte": Constructores y Memoria

Para que una variable de tipo `struct` sea una instancia, le faltaría un mecanismo de **inicialización automática** (el constructor). En C, tras hacer un `malloc` de una `struct`, los datos contienen basura hasta que los inicializas manualmente. Una instancia de una clase, por definición, nace mediante un constructor que garantiza un estado inicial válido.

Además, en Java, las instancias tienen **identidad gestionada** por la Máquina Virtual. Mientras que una variable de `struct` en C es solo un trozo de memoria que tú debes liberar con `free`, una instancia en Java es un objeto con un ciclo de vida controlado por el Recolector de Basura, lo que le otorga una "existencia" más abstracta y segura que la simple gestión de punteros en C.

---
## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

Para "quitar la magia" y entender qué ocurre bajo el capó en Java, podemos intentar replicar el comportamiento de la clase `Punto` en C. La clave está en entender que, aunque en C las funciones no pueden estar *dentro* de la estructura, podemos simular esa asociación mediante punteros.

Aquí se detalla cómo se emularía este comportamiento:

### La emulación en C

Para imitar una clase, definiríamos una `struct` para los datos y una función externa para la lógica. El "truco" para que la función sepa sobre qué objeto actuar es pasarle un puntero a la propia estructura como primer argumento.

```c
#include <stdio.h>
#include <math.h>

// La "Clase" en C es solo la estructura de datos
typedef struct {
    double x;
    double y;
} Punto;

// El "Método" es una función externa que recibe el "this" explícitamente
double calculaDistanciaAOrigen(Punto* self) {
    // En C usamos 'self' o 'p' manualmente
    return sqrt(self->x * self->x + self->y * self->y);
}

int main() {
    // Instanciación manual
    Punto miPunto;
    miPunto.x = 3.0;
    miPunto.y = 4.0;

    // Llamada al "método" pasando la dirección del objeto (el puntero 'this')
    double d = calculaDistanciaAOrigen(&miPunto);
    printf("Distancia: %f", d);
    return 0;
}

```

### ¿Qué ha pasado con `this`?

En C, el concepto de `this` no desaparece, simplemente **deja de ser invisible**. Como se observa en el código anterior, hemos tenido que pasar explícitamente el puntero `&miPunto` a la función. En lenguajes como Java o C++, el compilador hace este trabajo por nosotros: cada vez que llamamos a un método de instancia, el sistema "inyecta" silenciosamente la dirección del objeto como un parámetro oculto.

Por tanto, `this` en Java es exactamente lo que en C sería el puntero `self` o `this` que pasamos manualmente a la función. La "magia" de la POO consiste en ocultar ese puntero para que el código sea más limpio y menos propenso a errores (como pasar el puntero de un objeto equivocado a una función).

### Diferencias en la invocación

En la emulación en C, la sintaxis es `funcion(objeto)`, lo que pone el énfasis en la **acción**. En Java, la sintaxis es `objeto.metodo()`, lo que pone el énfasis en el **sujeto**. Esta diferencia sintáctica refleja el cambio de paradigma: en C los datos son piezas de madera que una herramienta (la función) procesa; en Java, el objeto es un ente con "vida" propia al que se le pide que realice una tarea sobre sí mismo.

