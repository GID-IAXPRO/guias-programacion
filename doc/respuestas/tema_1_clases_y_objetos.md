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
La abstracción consiste en identificar qué información y qué comportamientos son relevantes de un objeto, ignorando detalles innecesarios. En Java, esta idea se materializa mediante clases que representan conceptos del problema.

El encapsulamiento se refiere a proteger los datos internos de un objeto, permitiendo el acceso solo a través de métodos específicos. En lenguajes como Java esto se logra usando modificadores como private y public

La herencia permite que una clase derive de otra y pueda reutilizar su código, ampliando o modificando su comportamiento. Por ejemplo, una clase Vehiculo de la cual heredan Coche o Moto. Frente a C/C++, donde sin orientación a objetos esto se haría manualmente con estructuras y funciones, en Java es un mecanismo integrado.

El polimorfismo permite que diferentes clases respondan de manera distinta a un mismo método o mensaje. Esto hace posible escribir código más genérico, donde una referencia a una clase base pueda manipular objetos de varias clases derivadas



## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

### Respuesta
C++ combina características de programación estructurada con orientación a objetos, permitiendo definir clases, utilizar herencia múltiple y gestionar manualmente la memoria. Aunque no es un lenguaje puramente orientado a objetos, ofrece herramientas muy potentes para modelar entidades y sus relaciones, lo que explica su amplia adopción en sistemas de alto rendimiento.

Python también es un lenguaje orientado a objetos, incluso aunque su sintaxis resulte extremadamente flexible y permita estilos de programación variados. En Python, todo es un objeto, y las clases se pueden crear de forma muy sencilla, lo que favorece el aprendizaje progresivo del paradigma y su aplicación en proyectos de distinta escala.

C#, desarrollado por Microsoft, incorpora una orientación a objetos muy uniforme y bien integrada, con una sintaxis cercana a Java. Este lenguaje destaca por su robustez y por el amplio ecosistema que lo acompaña, lo que lo convierte en una opción frecuente en el desarrollo de aplicaciones empresariales, videojuegos y servicios en la nube



## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

### Respuesta

La programación estructurada es un paradigma anterior a la orientación a objetos que organiza el código en bloques claramente definidos mediante estructuras de control como secuencias, decisiones (if, switch) y bucles (for, while).
Promueve dividir el código en funciones pequeñas y bien definidas, lo que simplifica la depuración y el mantenimiento

la programación modular da un paso más al organizar el programa en unidades independientes llamadas módulos. Cada módulo agrupa funciones y datos relacionados, estableciendo una especie de “caja” con responsabilidades concretas.
En lenguajes como C, esto se observa claramente separando archivos .h y .c
Este enfoque modular facilita el trabajo en equipo, la reutilización de código y la reducción de dependencias


## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

### Respuesta

El estado representa la información que el objeto almacena internamente, normalmente mediante variables o atributos. Este estado describe cómo es el objeto en un momento dado, de forma similar a cómo una estructura en C guarda datos

El comportamiento corresponde a las acciones que el objeto puede realizar, implementadas mediante métodos. Estos métodos permiten modificar el estado del propio objeto o interactuar con otros
La identidad es lo que permite distinguir un objeto de otro incluso aunque compartan el mismo estado y comportamiento. Cada objeto existe como una instancia única en memoria


## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

### Respuesta

Una clase puede entenderse como un molde o plantilla que describe cómo serán los objetos que se creen a partir de ella, similar a cómo una struct en C define un tipo. Esta definición no ocupa espacio en memoria para datos concretos
Un objeto, es una entidad concreta creada a partir de una clase, es su materialización en memoria, con su propio estado independiente del de otros objetos de la misma clase.

El término instancia se refiere precisamente a cada objeto creado a partir de una clase. Instanciar consiste en reservar memoria para un nuevo objeto y prepararlo para su uso siguiendo la definición de la clase. Se realiza normalmente usando la palabra clave new
No todos los lenguajes orientados a objetos manejan el concepto de clase. JavaScript emplea un enfoque basado en prototipos, donde los objetos se crean a partir de otros objetos sin necesidad de definir clases formales



## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

### Respuesta
En general, los objetos se almacenan en la memoria dinámica, también conocida como heap. Cuando se crea una instancia mediante mecanismos como new en Java, se reserva un espacio en esa zona para guardar su estado. variables locales o primitivas, que suelen almacenarse en la pila (stack)
En C++, un objeto puede almacenarse tanto en la pila como en el heap, dependiendo de cómo se declare. Java gestiona de manera uniforme los objetos en el heap, evitando que el programador tenga que decidir explícitamente dónde situarlos, lo que reduce errores.

La recolección de basura (o garbage collection) es un mecanismo automático que libera memoria ocupada por objetos que ya no están en uso. En Java, el programador no destruye objetos manualmente, ya que el sistema detecta cuándo no existe ninguna referencia hacia ellos y procede a liberar el espacio ocupado
Ventajas en cuanto a seguridad y simplicidad, pero también implica que el programador no tiene control exacto sobre el momento de la liberación de memoria



## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

### Respuesta
Un método es una función asociada a una clase y, por tanto, al comportamiento de los objetos creados a partir de ella
En programación estructurada las funciones existen de manera independiente 	         En programación orientada a objetos los métodos forman parte integral del objeto y actúan sobre su estado interno definiendo qué puede hacer un objeto, cómo interactúa con otros y cómo modifica sus atributos
La sobrecarga de métodos consiste en definir varios métodos con el mismo nombre, pero con distintas listas de parámetros. Esto permite que un mismo comportamiento general pueda adaptarse a diferentes tipos o cantidades de datos
Por ejemplo, una clase podría tener varios métodos sumar, uno que reciba dos enteros y otro que reciba tres, y el compilador elegirá automáticamente cuál ejecutar dependiendo de los argumentos utilizados en la llamada


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

### Respuesta

```
// Archivo: Punto.java
class Punto {
    // Atributos con visibilidad por defecto (package-private)
    double x;
    double y;

    // Método que calcula la distancia al origen (0,0)
    double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
}

// Ejemplo de uso
public class EjemploUsoPunto {
    public static void main(String[] args) {
        Punto p = new Punto();
        p.x = 3.0;
        p.y = 4.0;

        double d = p.calculaDistanciaAOrigen();
        System.out.println("Distancia al origen: " + d); // Debería imprimir 5.0
    }
}
```


## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

### Respuesta

El punto de entrada de un programa en Java es el método main, cuya firma estándar es public static void main(String[] args). Este método actúa como lugar inicial donde comienza la ejecución del programa, de forma similar a int main() en C

La palabra clave static indica que un método o atributo pertenece a la clase y no a una instancia concreta. Esto permite llamar al método main sin haber creado ningún objeto previamente, necesario para arrancar el programa desde cero.
El uso de static no se limita al método main. Puede aplicarse a métodos auxiliares, atributos compartidos entre todas las instancias o bloques de inicialización estáticos. Su función es ofrecer un comportamiento común y accesible de manera global dentro de la clase

Cuando static se combina con final, se obtiene un miembro constante cuyo valor no puede cambiar una vez asignado. En Java, esta combinación suele emplearse para declarar constantes simbólicas, como static final double PI = 3.14159


## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

### Respuesta
Para compilar y ejecutar desde línea de comandos se puede usar el siguiente flujo básico. Primero, se guarda el código en un archivo Hola.java con una clase pública del mismo nombre y un main válido. Luego, se compila con javac (genera .class) y se ejecuta con java (carga .class y lo corre en la JVM)

```
// Archivo: Hola.java
public class Hola {
    public static void main(String[] args) {
        System.out.println("Hola, Java desde la consola!");
    }
}
# 1) Compilar (genera Hola.class en el mismo directorio)
javac Hola.java

# 2) Ejecutar (usar el nombre de la clase, sin .class ni ruta de archivo)
java Hola
```
Java se compila a bytecode intermedio (mediante javac), y ese bytecode se ejecuta en la Máquina Virtual de Java (JVM). Usa compilación JIT (Just-In-Time) para traducir partes calientes del bytecode a código nativo en tiempo de ejecución

La Máquina Virtual de Java (JVM) es el entorno de ejecución que carga, verifica y ejecuta el bytecode. Proporciona independencia de plataforma (“write once, run anywhere”): el mismo .class puede ejecutarse en distintas plataformas siempre que exista una JVM compatible. Además, ofrece servicios de runtime como gestión de memoria, recolección de basura, seguridad, threads o el JIT

El bytecode es el formato binario intermedio al que javac traduce el código fuente; cada clase compilada se almacena en un fichero .class que contiene ese bytecode


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

### Respuesta

En Java, new es el operador que reserva memoria en el heap y crea una instancia de una clase, devolviendo una referencia al objeto recién creado. Al invocar new, la JVM ejecuta un constructor, un método especial encargado de inicializar el estado del objeto. A diferencia de los métodos normales, un constructor no tiene tipo de retorno (ni siquiera void) y su nombre coincide exactamente con el de la clase. Si no se define ninguno, Java proporciona un constructor por defecto (sin parámetros) que inicializa los atributos a valores por defecto según su tipo

El constructor puede estar sobrecargado, ofreciendo distintas formas de crear objetos con diferentes datos de entrada

```
public class Empleado {
    // Atributos (visibilidad por defecto podría usarse, pero se recomienda encapsular)
    private String dni;
    private String nombre;
    private String apellidos;

    // Constructor por defecto (sin parámetros)
    public Empleado() {
        // Inicialización básica (opcional)
        this.dni = "";
        this.nombre = "";
        this.apellidos = "";
    }

    // Constructor con parámetros (sobrecarga del constructor)
    public Empleado(String dni, String nombre, String apellidos) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellidos = apellidos;
    }

    // Getters (accesores) de ejemplo
    public String getDni() { return dni; }
    public String getNombre() { return nombre; }
    public String getApellidos() { return apellidos; }

    // Método útil para mostrar el estado del objeto
    @Override
    public String toString() {
        return "Empleado{dni='" + dni + "', nombre='" + nombre + "', apellidos='" + apellidos + "'}";
    }
}

// Ejemplo de uso
class Demo {
    public static void main(String[] args) {
        Empleado e1 = new Empleado(); // usa el constructor por defecto
        Empleado e2 = new Empleado("12345678A", "Ada", "Lovelace"); // usa el constructor con parámetros

        System.out.println(e1);
        System.out.println(e2);
    }
}
```



## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

### Respuesta

La referencia this en Java señala al objeto actual sobre el que se está ejecutando un método o un constructor. Sirve para diferenciar entre los atributos del objeto y las variables con el mismo nombre. Además, permite encadenar constructores (this(...)) y pasar la referencia(Cambia la variable, no una copia)
Python, Swift y Ruby emplean self como primer parámetro convencional de los métodos y en Visual Basic .NET se usa Me.

```
// Archivo: Punto.java
class Punto {
    double x; // visibilidad por defecto (package-private)
    double y;

    // Constructor principal
    Punto(double x, double y) {
        // 'this.x' y 'this.y' son los atributos del objeto
        // 'x' y 'y' son los parámetros del constructor
        this.x = x;
        this.y = y;
    }

    // Constructor que usa this(...) para reutilizar lógica
    Punto() {
        this(0.0, 0.0); // delega en el otro constructor
    }

    double calculaDistanciaAOrigen() {
        // 'this' es opcional aquí; se usa para claridad
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }

    // Método que traslada el punto sumando dx y dy
    void trasladar(double dx, double dy) {
        this.x += dx;
        this.y += dy;
    }
}
```


## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

### Respuesta
```
// Archivo: Punto.java
class Punto {
    // Atributos con visibilidad por defecto (package-private)
    double x;
    double y;

    Punto() {
        this(0.0, 0.0);
    }

    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }

    // Nuevo método: distancia entre 'this' y el punto 'otro'
    double distanciaA(Punto otro) {
        double dx = this.x - otro.x;
        double dy = this.y - otro.y;
        return Math.sqrt(dx * dx + dy * dy);
    }
}

// Ejemplo de uso
public class EjemploDistancia {
    public static void main(String[] args) {
        Punto p1 = new Punto(1.0, 2.0);
        Punto p2 = new Punto(4.0, 6.0);

        double d = p1.distanciaA(p2);
        System.out.println("Distancia entre p1 y p2: " + d); // Imprime 5.0
    }
}
```

## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

### Respuesta

Cuando se pasa un objeto (por ejemplo, un Punto), es una copia del valor de la referencia al objeto. Dentro del método se apunta al mismo objeto que existe fuera; cambiar los atributos del objeto dentro del método sí afecta al objeto observado desde fuera, porque ambos (el llamador y el método) operan sobre misma instancia en memoria. En cambio, reasignar la variable parámetro (hacer otro = new Punto(...)) solo cambia la copia local de la referencia

Con los tipos primitivos (como int, double, boolean), también se pasa por valor, pero en este caso el valor es el dato en sí (no una referencia). Por ello, si se recibe un int y se modifica dentro del método, no cambia el valor fuera 

```
void modificaPunto(Punto p) {
    // Cambia el estado del mismo objeto (efecto visible fuera)
    p.x = 100;
    p.y = 200;

    // Reasignar la referencia NO cambia el objeto externo
    p = new Punto(0, 0); // esta nueva referencia se pierde al salir del método
}

void modificaEntero(int n) {
    n = 42; // solo cambia la copia local; fuera, el valor original permanece
}
```

En resumen:
 
•	OBJETOS→ se pasa por valor la referencia, por lo que mutar el estado del objeto dentro del método es visible fuera

•	PRIMITIVOS→ se pasa por valor el dato, por lo que cualquier cambio dentro del método no se refleja fuera




## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

### Respuesta

El método toString() en Java es una función definida en la clase base java.lang.Object que devuelve una representación textual del objeto. Por defecto, retorna el nombre de la clase y un identificador hash, pero lo habitual es sobrescribirlo para ofrecer una descripción legible que incluya el estado del objeto (sus atributos)
C# también usa ToString(). En Python, el método análogo es __str__ (y __repr__ para una representación más técnica) C++ se puede lograr algo similar sobrecargando el operador << para std::ostream o usando funciones como std::to_string

```
class Punto {
    double x; // visibilidad por defecto (package-private)
    double y;

    Punto() {
        this(0.0, 0.0);
    }

    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }

    double distanciaA(Punto otro) {
        double dx = this.x - otro.x;
        double dy = this.y - otro.y;
        return Math.sqrt(dx * dx + dy * dy);
    }

    @Override
    public String toString() {
        return "Punto{x=" + x + ", y=" + y + "}";
    }
}

// Ejemplo de uso:
public class DemoToString {
    public static void main(String[] args) {
        Punto p = new Punto(3.5, -2.0);
        System.out.println(p);          // Usa implícitamente toString(): "Punto{x=3.5, y=-2.0}"
        System.out.println(p.toString()); // Llamada explícita (mismo resultado)
    }
}
```



## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


### Respuesta
Una clase se parece a un struct de C en el sentido de que ambos permiten agrupar varios datos bajo un mismo tipo compuesto pero la similitud se detiene ahí.
En una clase, los métodos forman parte del propio tipo y se invocan sobre las instancias, integrando datos y comportamiento; en un struct clásico, las funciones deben escribirse aparte y reciben la estructura como parámetro

También falta encapsulamiento: los struct no permiten ocultar información (privated)

Otro aspecto ausente es la inicialización automática mediante constructores. Una clase ofrece constructores que ejecutan lógica cada vez que se crea un objeto. Además, las clases permiten sobrecarga de métodos, sobrescritura, polimorfismo e incluso herencia, conceptos completamente ajenos a los struct.


## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

### Respuesta

Se puede “emular” una clase sencilla como Punto en C agrupando los datos en un struct y definiendo funciones que operen sobre ese struct. El cálculo de la distancia al origen se implementa como una función que recibe un Punto (por valor o por puntero) y devuelve un double. Para inicializar el struct de forma coherente se puede añadir una función “constructor” (no es un constructor real del lenguaje) que devuelve un Punto con los campos asignados. No existe encapsulamiento nativo: los campos son públicos

En este enfoque, lo que en Java sería this se convierte en un parámetro explícito de las funciones, normalmente un puntero al struct cuando se pretende modificar o evitar copias costosas. Así, en lugar de this.x, se usa p->x dentro de la función. Si la función solo lee el estado, puede recibirse el struct por valor (copia) o por puntero constante para evitar copias y dejar claro que no se modifica

```
// punto.h
#ifndef PUNTO_H
#define PUNTO_H

typedef struct {
    double x;
    double y;
} Punto;

// "Constructor" sencillo (solo una función de inicialización)
static inline Punto punto_crear(double x, double y) {
    Punto p;
    p.x = x;
    p.y = y;
    return p;
}

// Función que calcula la distancia al origen (solo lectura)
double punto_distancia_origen(const Punto* p);

// Función opcional: distancia entre dos puntos
double punto_distancia_a(const Punto* a, const Punto* b);

#endif // PUNTO_H

```
```
// punto.c
#include "punto.h"
#include <math.h>

double punto_distancia_origen(const Punto* p) {
    // Equivalente a this.x y this.y: aquí 'p' hace de "this"
    return sqrt(p->x * p->x + p->y * p->y);
}

double punto_distancia_a(const Punto* a, const Punto* b) {
    double dx = a->x - b->x;
    double dy = a->y - b->y;
    return sqrt(dx * dx + dy * dy);
}
```
```
// main.c
#include <stdio.h>
#include "punto.h"

int main(void) {
    Punto p = punto_crear(3.0, 4.0);
    double d0 = punto_distancia_origen(&p);
    printf("Distancia al origen: %.2f\n", d0); // 5.00

    Punto q = punto_crear(1.0, 2.0);
    double d = punto_distancia_a(&p, &q);
    printf("Distancia entre p y q: %.2f\n", d); // 2.83

    return 0;
}
```
