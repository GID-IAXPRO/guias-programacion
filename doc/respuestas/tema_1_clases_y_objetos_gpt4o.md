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

### Respuesta

Las cuatro características básicas de la Programación Orientada a Objetos (POO) son: **encapsulación**, **herencia**, **polimorfismo** y **abstracción**.

La **encapsulación** permite agrupar datos (atributos) y funciones (métodos) que operan sobre esos datos dentro de una misma unidad (la clase), controlando el acceso a los mismos mediante modificadores de visibilidad. La **herencia** permite crear nuevas clases a partir de clases existentes, reutilizando y extendiendo su comportamiento. El **polimorfismo** permite que objetos de diferentes clases puedan ser tratados de manera uniforme, respondiendo de forma distinta a una misma operación según su tipo específico. Finalmente, la **abstracción** consiste en modelar las características esenciales de los objetos del mundo real, ignorando los detalles innecesarios, lo que facilita el diseño de sistemas complejos mediante una representación simplificada.

Estas características permiten escribir código más modular, reutilizable y mantenible que en paradigmas anteriores como la programación estructurada.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

### Respuesta

Cuatro lenguajes populares que permiten la programación orientada a objetos son: **Java**, **C++**, **Python** y **C#**.

Java es un lenguaje puramente orientado a objetos donde prácticamente todo es un objeto. C++ añade características de POO a C, permitiendo usar tanto programación procedural como orientada a objetos. Python es un lenguaje interpretado multiparadigma con soporte completo para POO. C# es el lenguaje principal de la plataforma .NET de Microsoft, diseñado con POO como paradigma fundamental.


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

### Respuesta

La **programación estructurada** es un paradigma que surgió en los años 60-70 para mejorar la claridad y mantenibilidad del código, eliminando el uso indiscriminado de instrucciones `goto`. Se basa en tres estructuras de control básicas: secuencia (ejecución lineal de instrucciones), selección (condicionales como `if-else`) y repetición (bucles como `while`, `for`). Este paradigma promueve dividir el programa en funciones o procedimientos, facilitando la comprensión del flujo del programa. Lenguajes como C son ejemplos de lenguajes estructurados.

La **programación modular** es un paso más allá que organiza el código en módulos o unidades independientes, cada una con una funcionalidad específica y bien definida. Cada módulo tiene una interfaz pública (lo que otros módulos pueden usar) y una implementación privada (detalles internos ocultos). Esto permite trabajar en diferentes partes del programa de forma independiente, facilita la reutilización de código y mejora el mantenimiento. La programación orientada a objetos puede verse como una evolución natural de la programación modular, donde los módulos son clases que encapsulan tanto datos como las funciones que operan sobre ellos.

## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

### Respuesta

Un objeto en programación orientada a objetos se define por tres elementos fundamentales: **identidad**, **estado** y **comportamiento**.

La **identidad** es lo que distingue a un objeto de otro, incluso si tienen el mismo estado. Es la dirección o referencia en memoria que lo identifica de forma única. El **estado** está definido por los valores de sus atributos o propiedades en un momento dado; por ejemplo, un objeto `Coche` podría tener atributos como color, velocidad y marca. El **comportamiento** está determinado por los métodos u operaciones que el objeto puede realizar o que se pueden realizar sobre él; siguiendo el ejemplo del `Coche`, podría tener métodos como `acelerar()`, `frenar()` o `cambiarMarcha()`.

Estos tres elementos juntos permiten modelar entidades del mundo real o conceptos abstractos de manera coherente dentro de un programa.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

### Respuesta

Una **clase** es una plantilla o molde que define la estructura y comportamiento que tendrán los objetos creados a partir de ella. Define qué atributos tendrán los objetos y qué métodos podrán ejecutar. No es lo mismo que un objeto: la clase es la definición abstracta, mientras que el objeto es una entidad concreta en memoria. Se puede pensar en la clase como el plano de una casa y el objeto como una casa construida según ese plano.

Una **instancia** es simplemente otro nombre para referirse a un objeto creado a partir de una clase. Cuando se crea un objeto, se dice que se "instancia" la clase. Pueden existir múltiples instancias de la misma clase, cada una con su propio estado pero compartiendo la misma estructura y comportamiento definidos en la clase.

No todos los lenguajes orientados a objetos manejan el concepto de clase. Existen lenguajes basados en **prototipos** como JavaScript (en su forma original) donde los objetos se crean a partir de otros objetos, sin necesidad de clases. Sin embargo, lenguajes como Java, C++ y C# sí se basan fundamentalmente en clases.


## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

### Respuesta

En la mayoría de lenguajes orientados a objetos, los objetos se almacenan en una zona de memoria dinámica llamada **heap** (montículo o memoria dinámica), similar a la memoria reservada con `malloc()` en C. Las variables que hacen referencia a estos objetos (las referencias o punteros) se suelen almacenar en la pila (stack), aunque esto puede variar según el lenguaje y el contexto. No es igual en todos los lenguajes: en C++, por ejemplo, los objetos pueden crearse tanto en la pila como en el heap, mientras que en Java todos los objetos se crean obligatoriamente en el heap.

La **recolección de basura** (garbage collection) es un mecanismo automático de gestión de memoria que libera la memoria ocupada por objetos que ya no son accesibles o utilizables por el programa. En lenguajes como C o C++, el programador debe liberar manualmente la memoria con `free()` o `delete`, lo que puede provocar fugas de memoria o errores si no se hace correctamente. En cambio, lenguajes como Java, C# o Python incluyen un recolector de basura que detecta automáticamente cuándo un objeto ya no tiene referencias y libera su memoria.

Esto simplifica significativamente la programación al eliminar una fuente común de errores, aunque introduce cierta sobrecarga en tiempo de ejecución y puede hacer que el comportamiento del programa sea menos predecible en términos de rendimiento.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

### Respuesta

Un **método** es una función asociada a una clase u objeto que define un comportamiento o acción que puede realizar. Es equivalente a una función en C, pero está vinculada a un tipo de dato específico (la clase) y puede acceder a los atributos del objeto sobre el que opera. Los métodos definen las operaciones que se pueden realizar con los objetos de una clase.

La **sobrecarga de métodos** (method overloading) es la capacidad de definir múltiples métodos con el mismo nombre dentro de una clase, pero con diferentes parámetros (distinto número de parámetros o distintos tipos). El compilador determina qué versión del método ejecutar en función de los argumentos proporcionados en la llamada. Por ejemplo, se podría tener un método `calcularArea(double radio)` para círculos y otro `calcularArea(double base, double altura)` para rectángulos. Esta característica no existe en C pero sí en C++ y Java, y permite crear interfaces más naturales y flexibles.


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

### Respuesta

```java
class Punto {
    double x;
    double y;
    
    double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
}

class EjemploUso {
    public static void main(String[] args) {
        Punto p = new Punto();
        p.x = 3.0;
        p.y = 4.0;
        double distancia = p.calculaDistanciaAOrigen();
        System.out.println("La distancia al origen es: " + distancia);
    }
}
```

La clase `Punto` define dos atributos de tipo `double` para las coordenadas. El método `calculaDistanciaAOrigen()` aplica el teorema de Pitágoras para calcular la distancia euclidiana desde el punto hasta el origen (0,0). La función `Math.sqrt()` es equivalente a `sqrt()` de la biblioteca matemática de C.

En el ejemplo de uso, se crea una instancia de `Punto` con el operador `new`, se asignan valores a sus coordenadas, y se invoca el método para obtener la distancia. El resultado será 5.0, ya que se trata de un triángulo rectángulo con catetos de 3 y 4 unidades.


## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

### Respuesta

El punto de entrada en un programa Java es el método `main`, que debe tener la firma específica: `public static void main(String[] args)`. Es equivalente a la función `main()` en C y es el primer método que se ejecuta cuando se inicia el programa.

La palabra clave `static` indica que un método o atributo pertenece a la clase en sí misma, no a una instancia particular de la clase. Los miembros estáticos pueden ser accedidos sin necesidad de crear un objeto. Por ejemplo, `Math.sqrt()` es un método estático de la clase `Math`. El método `main` debe ser estático porque cuando se inicia el programa, aún no existe ninguna instancia de la clase, y la máquina virtual necesita poder invocarlo directamente. `static` también se usa para definir constantes de clase, variables compartidas por todas las instancias, o métodos de utilidad que no necesitan acceder a datos de instancia.

La combinación `static final` se utiliza para definir constantes. `final` indica que el valor no puede cambiar después de su inicialización. Por ejemplo, `static final double PI = 3.14159;` define una constante de clase que es compartida por todas las instancias y cuyo valor es inmutable. Esta combinación es equivalente a usar `#define` o `const` en C/C++.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

### Respuesta

Para compilar un programa Java desde línea de comandos se usa `javac NombreArchivo.java`, que genera uno o más archivos `.class`. Para ejecutarlo se usa `java NombreClasePrincipal` (sin extensión). Por ejemplo:
```bash
javac EjemploUso.java
java EjemploUso
```

Java es un lenguaje **semi-compilado**. El compilador `javac` no genera código máquina nativo específico del procesador (como hace `gcc` con C), sino un código intermedio llamado **byte-code**, que se almacena en archivos `.class`. Este byte-code es independiente de la plataforma y no puede ejecutarse directamente por el procesador.

La **máquina virtual de Java** (JVM, Java Virtual Machine) es un programa que interpreta o compila en tiempo de ejecución (JIT compilation) el byte-code para convertirlo en instrucciones nativas del procesador. Esto permite que el mismo archivo `.class` se ejecute en Windows, Linux, Mac o cualquier sistema que tenga una JVM instalada, cumpliendo el principio "write once, run anywhere". Es análogo a tener un emulador que ejecuta un código intermedio. Esta arquitectura sacrifica algo de rendimiento a cambio de portabilidad y otras ventajas como la recolección de basura y mayor seguridad.


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

### Respuesta

El operador `new` reserva memoria en el heap para un nuevo objeto de la clase especificada, invoca el constructor correspondiente, y devuelve una referencia al objeto creado. Es similar a usar `malloc()` en C para reservar memoria, pero con la ventaja de que también inicializa el objeto automáticamente mediante el constructor.

Un **constructor** es un método especial que se ejecuta automáticamente cuando se crea una instancia de una clase con `new`. Su propósito es inicializar los atributos del objeto con valores específicos. El constructor tiene el mismo nombre que la clase y no tiene tipo de retorno (ni siquiera `void`). Si no se define ningún constructor, Java proporciona uno por defecto sin parámetros que inicializa los atributos con valores predeterminados (0 para números, `null` para referencias).

```java
class Empleado {
    String dni;
    String nombre;
    String apellidos;
    
    // Constructor
    Empleado(String dni, String nombre, String apellidos) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellidos = apellidos;
    }
}

// Ejemplo de uso:
Empleado emp = new Empleado("12345678A", "Juan", "García López");
```

Los constructores pueden estar sobrecargados, permitiendo crear objetos de diferentes formas según los parámetros proporcionados.


## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

### Respuesta

La referencia `this` es un puntero implícito que apunta al objeto actual sobre el que se está ejecutando un método. Permite acceder a los atributos y métodos del objeto desde dentro de sus propios métodos. Es equivalente al puntero implícito que se pasa a las funciones en C cuando se trabaja con estructuras, aunque en C hay que pasarlo explícitamente.

No se llama igual en todos los lenguajes: en Python se usa `self` (y debe declararse explícitamente como primer parámetro), en C++ y Java se usa `this`, mientras que en JavaScript también es `this` pero con semántica diferente según el contexto. El uso de `this` es especialmente útil cuando hay ambigüedad entre parámetros del método y atributos de la clase con el mismo nombre.

```java
class Punto {
    double x;
    double y;
    
    // Constructor usando this para diferenciar parámetros de atributos
    Punto(double x, double y) {
        this.x = x;  // this.x es el atributo, x es el parámetro
        this.y = y;
    }
    
    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }
}
```

Aunque en muchos casos `this` puede omitirse cuando no hay ambigüedad, usarlo explícitamente mejora la claridad del código.


## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

### Respuesta

```java
class Punto {
    double x;
    double y;
    
    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }
    
    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }
    
    double distanciaA(Punto otro) {
        double deltaX = this.x - otro.x;
        double deltaY = this.y - otro.y;
        return Math.sqrt(deltaX * deltaX + deltaY * deltaY);
    }
}

// Ejemplo de uso:
Punto p1 = new Punto(1.0, 2.0);
Punto p2 = new Punto(4.0, 6.0);
double dist = p1.distanciaA(p2);  // Calcula distancia de p1 a p2
System.out.println("Distancia: " + dist);  // Resultado: 5.0
```

El método `distanciaA` recibe otro punto como parámetro y calcula la distancia euclidiana entre el punto actual (`this`) y el punto proporcionado (`otro`). Se aplica la fórmula de la distancia entre dos puntos: $\sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$.


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

### Respuesta

En Java, el paso de parámetros siempre es **por valor**, pero el comportamiento puede parecer diferente según el tipo. Para objetos como `Punto`, lo que se copia es la **referencia** (el puntero) al objeto, no el objeto en sí. Por tanto, si dentro del método se modifican los atributos del objeto a través de la referencia (como `otro.x = 10`), estos cambios **sí afectan** al objeto original fuera del método, porque ambas referencias apuntan al mismo objeto en memoria. Sin embargo, si se reasigna la referencia misma (como `otro = new Punto(0, 0)`), esto no afecta a la referencia externa.

En el caso de tipos primitivos como `int`, el paso es por valor puro: se copia el valor del entero. Si se modifica el valor del parámetro dentro del método, el cambio no afecta a la variable original fuera del método. Esto es idéntico al comportamiento en C cuando se pasa un `int` directamente (sin puntero).

La diferencia clave es que en Java los objetos siempre se manejan mediante referencias (similar a punteros en C), mientras que los tipos primitivos se pasan y manejan directamente por valor. En C++, se tendría control explícito sobre esto mediante el uso de punteros, referencias (`&`) o paso por valor.


## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

### Respuesta

El método `toString()` es un método especial en Java que devuelve una representación en forma de cadena de texto del objeto. Se invoca automáticamente cuando se intenta imprimir un objeto o concatenarlo con una cadena. Todas las clases en Java heredan implícitamente este método de la clase `Object` (la clase raíz de la jerarquía), que por defecto devuelve el nombre de la clase y la dirección de memoria en formato hexadecimal. Sobrescribir este método permite proporcionar una representación más legible y útil del objeto.

Conceptos similares existen en otros lenguajes: en Python se usa `__str__()` o `__repr__()`, en C# se usa `ToString()`, y en C++ se puede sobrecargar el operador `<<` para lograr un efecto similar. No existe un equivalente directo en C estándar, donde habría que escribir funciones explícitas como `print_punto()` para imprimir estructuras.

```java
class Punto {
    double x;
    double y;
    
    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }
    
    @Override
    public String toString() {
        return "Punto(" + x + ", " + y + ")";
    }
}

// Ejemplo de uso:
Punto p = new Punto(3.5, 7.2);
System.out.println(p);  // Imprime: Punto(3.5, 7.2)
```

La anotación `@Override` indica que se está sobrescribiendo un método de la clase padre, ayudando a prevenir errores.


## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


### Respuesta
Un `struct` en C es conceptualmente similar a una clase, ya que agrupa datos relacionados bajo un mismo tipo. De hecho, C++ extiende el concepto de `struct` para que pueda contener métodos, convirtiéndolo esencialmente en una clase (la única diferencia es que en un `struct` los miembros son públicos por defecto, mientras que en una `class` son privados). Las variables de tipo `struct` podrían considerarse instancias en un sentido informal.

Sin embargo, al `struct` de C le faltan características fundamentales para ser una verdadera clase orientada a objetos. No puede contener funciones dentro de su definición (solo datos), carece de mecanismos de encapsulación (no hay modificadores de acceso como `private` o `public`), no soporta herencia ni polimorfismo, y no tiene constructores ni destructores automáticos. Tampoco hay vinculación directa entre las funciones y los datos: si se quiere operar sobre un `struct`, hay que escribir funciones separadas que reciban explícitamente punteros al `struct`.

En esencia, el `struct` de C proporciona solo agrupación de datos, mientras que una clase en POO integra datos y comportamiento en una unidad cohesiva con control de acceso y soporte para los pilares de la orientación a objetos.

## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

### Respuesta
```c
#include <math.h>
#include <stdio.h>

typedef struct {
    double x;
    double y;
} Punto;

// Función que "pertenece" conceptualmente a Punto
double Punto_calculaDistanciaAOrigen(Punto* this) {
    return sqrt(this->x * this->x + this->y * this->y);
}

int main() {
    Punto p;
    p.x = 3.0;
    p.y = 4.0;
    double distancia = Punto_calculaDistanciaAOrigen(&p);
    printf("Distancia al origen: %.2f\n", distancia);
    return 0;
}
```

Para emular una clase con `struct` en C, se define la estructura con los datos y se crean funciones separadas que operan sobre ella. Por convención, estas funciones suelen nombrarse con el prefijo del tipo (`Punto_`). Lo más importante es que el puntero `this` implícito en Java debe pasarse **explícitamente** como primer parámetro en C, recibiendo un puntero a la estructura.

Esto revela la "magia" de la POO: el compilador de Java automáticamente pasa el objeto actual como parámetro implícito a cada método, algo que en C debe hacerse manualmente. Esta es precisamente la forma en que lenguajes como C++ implementan internamente los métodos: convirtiendo `objeto.metodo()` en algo equivalente a `metodo(&objeto)` a nivel de compilación. La programación orientada a objetos proporciona sintaxis y abstracciones que facilitan trabajar con esta asociación entre datos y funciones de forma más natural y segura.
