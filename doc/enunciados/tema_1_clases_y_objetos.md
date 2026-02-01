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

La programación orientada a objetos se basa en cuatro características principales: Abstracción, Encapsulación, Herencia y Polimorfismo. La abstracción permite representar las características esenciales de un objeto. La encapsulación oculta los detalles internos y expone solo las operaciones necesarias. La herencia permite crear nuevas clases basadas en clases existentes. El polimorfismo permite que objetos de diferentes clases se comporten de manera uniforme.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

Java, Python, C++, C#


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

La programación estructurada se enfoca en la organización lógica del código, evitando saltos incondicionales y promoviendo la división en funciones pequeñas. Por otro lado, la programación modular divide un programa en módulos independientes que realizan funciones específicas, facilitando la comprensión y reutilización del código. Ambos enfoques buscan hacer el código más legible, mantenible y menos propenso a errores.

## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

En programación orientada a objetos, un objeto se caracteriza por su estado, comportamiento y identidad. El estado se refiere a sus atributos, como el color o marca, que pueden cambiar con el tiempo. El comportamiento se define a través de sus métodos, como acelerar o frenar, que indican las acciones que puede llevar a cabo. La identidad de un objeto se refiere a su unicidad dentro del sistema, determinada por su dirección de memoria. En resumen, un objeto en programación orientada a objetos se define por sus propiedades, acciones y singularidad en el sistema.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

En programación, una **clase** es un modelo que define atributos y comportamientos compartidos por objetos creados a partir de ella, sin representar un objeto real. Un **objeto** es una instancia concreta de una clase, representando una entidad específica con un estado y acciones definidos por la clase. Una **instancia** es un objeto creado a partir de una clase, estableciendo una relación concreta entre ambos. La mayoría de los lenguajes orientados a objetos como Java, C++, Python, Ruby y C# utilizan clases, mientras que algunos como JavaScript usan prototipos en lugar de clases.


## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

Los objetos en memoria se almacenan en diferentes áreas dependiendo del lenguaje de programación y su modelo de gestión. En muchos lenguajes, se guardan en el heap, una región dinámica donde se asigna memoria durante la ejecución. Algunos lenguajes requieren que el programador gestione la asignación y liberación de memoria, como C o C++, mientras que otros, como Java y Python, utilizan la recolección de basura para gestionar automáticamente la memoria. Este proceso libera la memoria ocupada por objetos inaccesibles, evitando problemas como fugas de memoria. La recolección de basura rastrea las referencias a los objetos para determinar cuáles ya no son necesarios y luego libera su memoria para reutilización.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

En la programación orientada a objetos, un método es una función asociada a un objeto o clase que define su comportamiento y permite realizar operaciones específicas accediendo y modificando el estado interno del objeto. Los métodos son esenciales para la encapsulación y se definen dentro de las clases en muchos lenguajes de programación. La sobrecarga de métodos permite definir múltiples métodos con el mismo nombre pero diferentes parámetros en una clase, facilitando la creación de interfaces más intuitivas y versátiles al permitir el uso de un nombre lógico para funciones similares que se diferencia por los parámetros utilizados.


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

```java
public class Punto {
    // Atributos con visibilidad por defecto
    int x;
    int y;
    
    // Constructor
    public Punto(int x, int y) {
        this.x = x;
        this.y = y;
    }
    
    // Método para calcular la distancia al origen (0,0)
    public double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    // Método main para probar la clase
    public static void main(String[] args) {
        // Crear un punto en la posición (3, 4)
        Punto punto = new Punto(3, 4);
        // Calcular y mostrar la distancia al origen
        double distancia = punto.calculaDistanciaAOrigen();
        System.out.println("La distancia al origen es: " + distancia);
    }
```

## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

En Java, el método `main` es el punto de entrada de un programa y debe tener la firma `public static void main(String[] args)`. Los términos asociados son: `public` para indicar accesibilidad desde cualquier clase, `static` para pertenecer a la clase en lugar de una instancia específica, `void` para indicar que no devuelve valor, `main` como nombre del método de entrada y `String[] args` como parámetro para pasar argumentos desde la línea de comandos. El modificador `static` se puede aplicar a variables, métodos y bloques de inicialización, permitiendo llamar al método `main` sin crear una instancia de clase. También se combina con `final` para crear constantes inmutables en la clase.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

Para compilar y ejecutar un programa Java desde la línea de comandos, primero escribe el código fuente en un archivo `.java`. Luego, compila el programa usando el comando `javac MiPrograma.java` para generar un archivo `MiPrograma.class`. Finalmente, ejecuta el programa con `java MiPrograma` para ver el mensaje "¡Hola, mundo!" impreso en la consola. Java se compila a bytecode para la JVM, que interpreta y ejecuta el código. La JVM es esencial para ejecutar aplicaciones Java, proporcionando portabilidad y gestionando la memoria y recolección de basura. Es compatible con diferentes plataformas y sistemas operativos, traduciendo el bytecode a instrucciones del hardware.


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

En el código, `new` en Java se usa para crear una nueva instancia de un objeto, como en `new Punto`. El constructor `public Punto(int x, int y)` de la clase `Punto` se utiliza para inicializar las coordenadas de un punto con valores proporcionados. Por lo tanto, `new Punto(3, 4)` crea un nuevo objeto `Punto` con coordenadas 3 y 4.


## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

La palabra clave `this` se usa en varios lenguajes de programación para referirse al objeto actual en una clase, permitiendo distinguir entre campos de la instancia actual y variables locales. No todos los lenguajes usan `this`; en Java y C++ se usa, en Python es `self` y en JavaScript se mantiene `this`. Aunque común en lenguajes orientados a objetos, la sintaxis puede variar, con diferencias en nombre y uso específicos.


## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

```java
public class Punto {
    private int x;
    private int y;

    // Constructor
    public Punto(int x, int y) {
        this.x = x;
        this.y = y;
    }

    // Método para calcular la distancia entre dos puntos
    public double distanciaA(Punto otroPunto) {
        int deltaX = this.x - otroPunto.getX();
        int deltaY = this.y - otroPunto.getY();
        return Math.sqrt(deltaX * deltaX + deltaY * deltaY);
    }

    // Otros métodos y atributos de la clase Punto
    // ...
    // Métodos getter para obtener las coordenadas x e y
    public int getX() {
        return x;
    }
    public int getY() {
        return y;
    }
}
```


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

En Java, los argumentos primitivos se pasan por valor, lo que significa que los cambios en esos valores dentro de un método no afectan al valor original. En cambio, al pasar un objeto como parámetro, se pasa una copia de la referencia al objeto. Aunque la referencia se pase por valor, los cambios en el objeto dentro del método se reflejarán fuera del mismo. Por lo tanto, al modificar atributos de un objeto `Punto`, los cambios se verán en la instancia original debido a que la referencia se pasa por valor.



## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

`toString()` en Java es un método de la clase `Object` que devuelve una representación de cadena del objeto. La implementación por defecto muestra el nombre de la clase seguido de `@` y el hash hexadecimal. Clases personalizadas suelen anular este método para una representación más útil. En Python, `__str__()` es similar a `toString()`.


## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


Una clase en Java es similar a un `struct` en C ya que ambas son estructuras de datos con múltiples campos, pero difieren en varios aspectos. En Java, una clase encapsula datos y métodos, permitiendo la encapsulación, mientras que en C los datos suelen estar expuestos. Además, las clases en Java admiten herencia y polimorfismo, conceptos ausentes en los `structs` de C. En Java, los campos pueden ser privados y accedidos mediante métodos, lo que controla su modificación. Las clases en Java también tienen constructores para inicializar objetos y no tienen destructores, a diferencia de los `structs` en C. En resumen, las clases de Java ofrecen más funcionalidades y control sobre los objetos que los `structs` de C.


## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

Definir una estructura `Punto` en C con coordenadas `x` e `y` y crear funciones operativas para emular el comportamiento de una clase `Punto`. Aunque este enfoque emula la funcionalidad básica de una clase `Punto`, no incluye características avanzadas de la programación orientada a objetos como encapsulación, herencia y polimorfismo presentes en lenguajes como Java.
