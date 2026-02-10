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

ABSTRACCIÓN: se permite el olvido de detalles, enfocándose solo en lo esencial, con el fin de tratar temas complejos

ENCAPSULACIÓN: se oculta la implementación interna de un objeto, exponiendo así sólo una interfaz pública para interactuar con él.

HERENCIA: se crean clases basándose en otras existentes, herendando así atributos y métodos. De este modo se facilita la creación de jerarquías y la reutilización de código, donde las clases hijas pueden extender o modificar el comportamiento de las clases superiores.

POLIMORFISMO: capacidad de los objetos de tomar distintas formas dependiendo del contexto. De este modo métodos con el mismo nombre se comportan de forma diferente dependiendo del objeto que los invoque.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

DINÁMICOS: python, javaScript
En un lenguaje dinámico muchas de sus características, como los tipos de datos y la estructura de los objetos, pueden cambiar en tiempo de ejecución.

ESTÁTICOS: 
    -Con GC: Java, C#
    -Sin GC: C++
En un lenguaje estático los tipos y estructuras se determinan antes de la ejercución del programa.
  *GC (Garbage Colector): se encarga automáticamente de liberar la memoria que ya no está siendo utilizada por el programa, eliminando objetos y datos que dejaron de ser accesibles.

## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

PROGRAMACIÓN ESTRUCTURADA: es un paradigma de la programación que surgió antes de la programación orientada a objetos. El objetivo principal es mejorar la claridad, calidad y desarrollo de los programas a través del uso de estructuras de control bien definidas:
    -secuencia
    -selección (if/else, switch)
    -repetición (for, while).
Se evita el uso de instrucciones “goto”, favoreciendo el flujo de control ordenado. De este modo se facilita la comprensión y el mantenimiento del código.

PROGRAMACIÓN MODULAR: es una evolución del paradigma estructurado. Consiste en dividir el sistema en módulos independientes, cada uno encargado de una parte específica de la funcionalidad. Cada módulo puede desarrollarse, probarse y mantenerse por separado, lo que mejora la organización, reutilización y escalabilidad del código.

## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

ESTADO (atributos o propiedades): son los datos o características que describen al objeto en un momento dado.

COMPORTAMIENTO (métodos): las acciones o funciones que el objeto puede realizar.

IDENTIDAD: es la propiedad que distingue a cada objeto de los demás aunque existan objetos con el mismo estado y comportamiento. En muchos lenguajes está ligada a la dirección de memoria.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

Una CLASE permite describir las características (atributos o propiedades) y comportamientos (métodos o funciones) que tendrán los objetos creados a partir de ella, como un "molde" (En C++ sería como un struct).
Los OBJETOS son las variables tipo de la clase, se crean a partir de ella.

Una INSTANCIA es un objeto creado a partir de una clase. El término “instanciar” significa crear (en memoria) un objeto específico usando una clase como molde.

## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

No todos los lenguajes orientados a objetos manejan el concepto de clase. Existen lenguajes orientados a objetos basados en prototipos, como JavaScript, donde el concepto principal es el objeto en sí, y no la clase. En estos lenguajes, los objetos pueden heredar directamente de otros objetos (prototipos)

Generalmente, los objetos se almacenan en el área de memoria llamada “heap” (o montón). El heap es una zona de la memoria que se usa para almacenar datos cuyo tamaño o tiempo de vida no se conoce durante la compilación, es decir, para datos dinámicos, como los objetos en POO.
    *Cuando creas un objeto con "new" (en Java, C#, C++, etc.), normalmente se reserva memoria en el heap.

No es exactamente igual en todos los lenguajes.
    -En lenguajes como Java, C# o Python, los objetos suelen almacenarse en el heap, y se accede a ellos mediante referencias/punteros.
    -En lenguajes como C++ los objetos pueden almacenarse tanto en el heap (se utiliza new y debe liberarse manualmente) como en la pila / call stack (no se usa new, se almacena en la pila y se destruye automáticamente.
    .En lenguajes como javaScript el programador no tiene que gestionar la reserva, uso y liberación de la memoria utilizada por objetos o datos del programa (manejo de memoria abstraído). Pero en la práctica los objetos suelen estar en el heap.

## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

Un MÉTODO es una función que está definida dentro de una clase y que describe una acción o comportamiento que pueden realizar los objetos de esa clase. En otras palabras, los métodos son las “operaciones” asociadas a un tipo de objeto en la programación orientada a objetos.

La SOBRECARGA DE MÉTODOS es una característica que permite tener varios métodos con el mismo nombre dentro de una misma clase, siempre y cuando tengan una diferencia en el número o tipo de parámetros (la “firma” del método es distinta).

## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

// Estado (atributos)
    class Punto {
        int x;
        int y;

        // Comportamiento (métodos)
        double calcularDistanciaAOrigen(){
            return Math.sqrt(this.x * this.x + this.y * this.y);
        }
    }

public class EjercicioTeoria8 {
    public static void main(String[] args) {

        Punto mipunto = new Punto();
        mipunto.x = 5;
        mipunto.y = 6;

        double aOrigen = mipunto.calcularDistanciaAOrigen();
        System.out.println("Distancia a origen: " + aOrigen);
    }
}

## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

El PUNTO DE ENTRADA en un programa Java es el método: public static void main(String[] args)
  *STATIC indica que un miembro de la clase (atributo o método) pertenece a la clase y no a una instancia concreta.
Esto implica que existe una sola copia compartida para toda la clase.
Se puede utilizar en otros contextos además del main:
      -MÉTODOS ESTÁTICOS: no dependen del estado de ningún onjeto, solo de la clase.
      -ATRIBUTOS ESTÁTICOS: variables compartidas por todas las instancias de la clase.
      -BLOQUES ESTÁTICOS: Fragmentos de código que se ejecutan una vez al cargar la clase.
      -CLASES INTERNAS ESTÁTICAS: clases anidadas.
Se combina con final para definir ATRIBUTOS CONSTANTES DE CLASE (valores que no pueden cambiar y pertenecen a la clase, no a las instancias.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

Se crea un archivo con el mismo normbre que la clase pública (nombre archivo). Después ejecutamos en la línea de comandos “javac HolaMundo.java” (genera un archivo .class y java nombreArchivo.
Java es un lenguaje compilado a bytecode, no a código máquina como C o C++, lo que se denomina compilación a dos niveles.
Código Java (.java)
        ↓
    javac (compilador)
        ↓
    Bytecode (.class)
        ↓
    JVM (máquina virtual)
        ↓
    Código máquina nativo
La java virtual machine (JVM) es un intérprete/compilador virtual que ejecuta el bytecode, un programa que simula una computadora ficticia en tu sistema operativo y lo que hace que java sea multiplataforma.
El bytecode es un código interno que depende del procesador, por lo tanto no es código máquina específico y tampoco es un código fuente legible como el .java . Es un formato comprimido que la JVM puede ejecutar rápidamente. Para visualizarlo se utiliza javap.

## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

“new” es una palabra clave (operador) que crea una nueva instancia (objeto) de una clase en memoria, reserva espacio en memoria para el objeto, llama al constructor de la clase y devuelve una referencia al objeto creado.
Un constructor es un método especial que se llama automáticamente cuando se crea un objeto con “new”. Se utiliza para inicializar los atributos del objeto, tiene el mismo nombre que la clase y NO devuelve nada.

Ejemplo: 

public class MiClase {
    // Constructor
    public MiClase() {
        // Código de inicialización
    }
}

## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

“this” es una referencia que apunta al objeto actual (la instancia en la que se ejecuta el código), permite acceder a los atributos y métodos del objeto, se usa para diferenciar atributos de parámetros con el mismo nombre y permite pasar el objeto a otros métodos.
No se llama igual en todos los lenguajes:

Java: this
Python: self
C++: this (puntero)
C#: this
JavaScript: this
PHP: $this
Ruby: self

Ejemplo:
public class Punto {
    // Atributos
    private int x;
    private int y;
    
    // ===== CASO 1: Diferenciar atributo de parámetro =====
    public Punto(int x, int y) {
        // Sin this sería confuso:
        // x = x;  ← ¿cuál x es cuál?
        
        // Con this es claro:
        this.x = x;  // atributo = parámetro
        this.y = y;
    }
    
    // ===== CASO 2: Usar this en métodos =====
    public void trasladar(int dx, int dy) {
        this.x += dx;  // Modificar atributos de este objeto
        this.y += dy;
    }
    
    // ===== CASO 3: Acceder a métodos con this =====
    public void mostrarInfo() {
        System.out.println("Punto: (" + this.getX() + ", " + this.getY() + ")");
        // 'this.' es opcional aquí, pero puede ser explícito
    }
    
    // ===== CASO 4: Pasar this a otros métodos =====
    public void compararCon(Punto otro) {
        if (this.distancia() == otro.distancia()) {
            System.out.println("Ambos puntos están a la misma distancia del origen");
        }
    }
    
    // ===== CASO 5: Devolver this (para encadenamiento) =====
    public Punto sumarPunto(Punto otro) {
        this.x += otro.x;
        this.y += otro.y;
        return this;  // Devuelve el mismo objeto modificado
    }
    
    // ===== CASO 6: Llamar a otros constructores con this =====
    // (veremos después)
    
    // Métodos auxiliares
    public int getX() {
        return this.x;
    }
    
    public int getY() {
        return this.y;
    }
    
    public double distancia() {
        // Distancia al origen (0, 0)
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }
    
    public static void main(String[] args) {
        // Crear puntos
        Punto p1 = new Punto(3, 4);      // Usa constructor con this
        Punto p2 = new Punto(1, 2);
        
        // Caso 2: Usar this en métodos
        System.out.println("=== Caso 2: Trasladar ===");
        p1.mostrarInfo();                // (3, 4)
        p1.trasladar(2, 3);              // this.x += 2, this.y += 3
        p1.mostrarInfo();                // (5, 7)
        
        // Caso 3: Acceder a métodos
        System.out.println("\n=== Caso 3: Mostrar Info ===");
        p2.mostrarInfo();
        
        // Caso 4: Pasar this a otros métodos
        System.out.println("\n=== Caso 4: Comparar ===");
        System.out.println("Distancia de p1: " + p1.distancia());
        System.out.println("Distancia de p2: " + p2.distancia());
        p1.compararCon(p2);
        
        // Caso 5: Encadenamiento con return this
        System.out.println("\n=== Caso 5: Encadenamiento ===");
        Punto p3 = new Punto(2, 2);
        p3.mostrarInfo();
        p3.sumarPunto(new Punto(3, 1)).mostrarInfo();  // Encadenamiento
    }
}

## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

public class PuntoConThis {
    private int x;
    private int y;
    
    // Constructor 1: sin parámetros
    public PuntoConThis() {
        // Llamar al constructor con parámetros usando this()
        this(0, 0);  // Llama al constructor de abajo
    }
    
    // Constructor 2: con parámetros
    public PuntoConThis(int x, int y) {
        this.x = x;
        this.y = y;
        System.out.println("Punto creado en (" + x + ", " + y + ")");
    }
    
    // Constructor 3: con un parámetro
    public PuntoConThis(int valor) {
        this(valor, valor);  // Llama al constructor con dos parámetros
    }
    
    public static void main(String[] args) {
        new PuntoConThis();           // Constructor 1 → Constructor 2
        new PuntoConThis(5);          // Constructor 3 → Constructor 2
        new PuntoConThis(3, 4);       // Constructor 2
    }
}

## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

El Punto se pasa por referencia, ambas variables (original y parámetro) apuntan al mismo objeto en memoria. Entonces, si cambias los atributos del Punto dentro del método , estos cambios sí afectan al objeto original fuera del método.
Si pasas un int y lo modificas dentro del método, los cambios NO afectan al original fuera del método. Esto es porque los int se pasan por copia del valor

## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

El método toString() es un método especial que convierte un objeto a una representación en forma de texto (string), se ejecuta automáticamente cuando se intenta imprimir un objeto, viene heredado de la clase Object y puede ser sobrescrito para personalizar cómo se ve el objeto. 

Existe en otros lenguajes:
Java:
@Override
public String toString() {
    return "Punto(" + x + ", " + y + ")";
}
Python:
def __str__(self):
    return f"Punto({self.x}, {self.y})"

# O también:
def __repr__(self):
    return f"Punto({self.x}, {self.y})"
C++:
std::string toString() const {
    return "Punto(" + std::to_string(x) + ", " + 
           std::to_string(y) + ")";
}

// O sobrescribir el operador <<
friend std::ostream& operator<<(std::ostream& os, const Punto& p) {
    os << "Punto(" << p.x << ", " << p.y << ")";
    return os;
}
C#:
public override string ToString() {
    return $"Punto({x}, {y})";
}
JavaScript:
toString() {
    return `Punto(${this.x}, ${this.y})`;
}

// O:
[Symbol.toStringTag]() {
    return `Punto(${this.x}, ${this.y})`;
}

Ejemplo:
public class Punto {
    private int x;
    private int y;
    
    public Punto(int x, int y) {
        this.x = x;
        this.y = y;
    }
    
    // Sobrescribir toString()
    @Override
    public String toString() {
        return "Punto(" + x + ", " + y + ")";
    }
    
    public static void main(String[] args) {
        Punto p1 = new Punto(5, 10);
        Punto p2 = new Punto(-3, 7);
        Punto p3 = new Punto(0, 0);
        
        // Ahora se ve mucho mejor
        System.out.println(p1);
        System.out.println(p2);
        System.out.println(p3);
        
        // También funciona en concatenación
        System.out.println("El primer punto es: " + p1);
    }
}

## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


Sí, una clase en java es similar a un struct en C, pero con algunas diferencias fundamentales:

Clase (Java):
-Agrupa datos
-Contiene métodos
-Encapsulación
-Tiene constructores
-Herencia
-Polimorfismo
-Control de acceso (privado o público)
-Destructores
De todas esas características el struct en C solo presenta la primera, por lo que le faltarían los métodos, la encapsulación, los constructores, la herencia y el polimorfismo.

## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

En C++:
#include <stdio.h>
#include <math.h>

// STEP 1: Definir la estructura (datos)
typedef struct {
    int x;
    int y;
} Punto;

En Java:
public class Punto {
    private int x;
    private int y;
    
    public Punto(int x, int y) {
        this.x = x;
        this.y = y;
    }
    
    public double distancia() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }
    
    public void mostrar() {
        System.out.println("Punto: (" + this.x + ", " + this.y + ")");
    }
}

En java “this” es implícito, es decir, el compilador lo añade automáticamente. En C no existe, hay que pasar el struct.
