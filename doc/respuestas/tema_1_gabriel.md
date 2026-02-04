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

La abstracción permite centrarse en los aspectos esenciales de un elemento, dejando fuera los detalles irrelevantes. Gracias a ella, se pueden representar conceptos complejos de forma más simple. 

La encapsulación combina datos y métodos en una misma clase y regula qué partes deben ser públicas o internas.

La herencia permite crear nuevas clases a partir de otras ya existentes, reutilizando atributos y métodos. 

Por último, el polimorfismo hace posible que métodos con el mismo nombre se comporten de forma distinta dependiendo del tipo concreto del objeto que los invoque.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

### Respuesta

Son ejemplos de lenguajes orientados a objetos Java, C++, Python y JavaScript. Aunque todos soportan clases y objetos, cada uno lo hace con un enfoque diferente.

Estos lenguajes permiten estructurar programas como colecciones de objetos con estado y comportamiento, una idea central de la programación orientada a objetos.


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

### Respuesta

La programación estructurada organiza el código usando secuencia, selección e iteración, evitando saltos no controlados como goto. Este enfoque mejora la claridad y la facilidad de mantenimiento del programa.

La programación modular divide el software en módulos independientes, cada uno con una responsabilidad concreta. Esto facilita la reutilización, la depuración y el trabajo en equipo.


## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

### Respuesta

En programación orientada a objetos, un objeto se define principalmente por sus atributos, que representan los datos o características que describen su estado interno. Estos atributos contienen los valores que diferencian a una instancia de otra, incluso cuando ambas pertenecen a la misma clase.

También se define por sus métodos, que son las acciones o comportamientos que puede realizar, y por su estado, que es el conjunto de valores actuales de sus atributos en un momento dado. El estado cambia cuando los métodos modifican dichos atributos, lo que permite que el objeto evolucione durante la ejecución del programa.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

### Respuesta

Una clase es una plantilla o modelo que define qué atributos y métodos tendrán los objetos creados a partir de ella. Describe la estructura y el comportamiento común que compartirán todas sus instancias, pero por sí misma no ocupa memoria durante la ejecución del programa. Funciona como un plano que indica cómo deben construirse los objetos.

Un objeto no es lo mismo que una clase; es una instancia, es decir, un ejemplar concreto creado a partir de la clase. Cada instancia tiene sus propios valores de atributos y puede ejecutar los métodos definidos en la clase. Mientras que la clase describe, el objeto existe realmente en memoria y puede manipularse durante la ejecución.

No todos los lenguajes orientados a objetos utilizan el concepto de clase de la misma forma. Lenguajes como Java, C++ o C# siguen un modelo basado en clases, mientras que otros, como JavaScript, pueden funcionar con prototipos en lugar de clases tradicionales. Aun así, todos persiguen representar entidades mediante objetos con datos y comportamiento asociado.



## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

### Respuesta

En la mayoría de lenguajes orientados a objetos, los objetos se almacenan en el heap, una zona de memoria dinámica que permite que existan más allá del bloque donde se crean. Sin embargo, el comportamiento no es idéntico en todos los lenguajes: por ejemplo, en C++ algunos objetos pueden alojarse también en el stack, mientras que en Java todos los objetos se crean siempre en el heap.

La recolección de basura es un sistema automático que libera la memoria de los objetos que ya no se usan. Este proceso evita fugas de memoria y elimina la necesidad de que el programador gestione la liberación manualmente, como ocurre en C o C++.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

### Respuesta

Un método es una función asociada a una clase que describe acciones que pueden realizar sus objetos. Define el comportamiento de las instancias.

La sobrecarga consiste en tener varios métodos con el mismo nombre pero distintos parámetros. Esto permite ofrecer varias versiones de una misma operación sin necesidad de cambiar su nombre.



## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

### Respuesta

```java
public class Punto {

    // Atributos con visibilidad por defecto (sin public ni private)
    double x;
    double y;

    // Método que calcula la distancia del punto al origen (0,0)
    public double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    // Ejemplo de uso dentro de main
    public static void main(String[] args) {

        // Crear una instancia de Punto
        Punto p = new Punto();

        // Asignar valores a x e y
        p.x = 3;
        p.y = 4;

        // Llamar al método y guardar el resultado
        double distancia = p.calculaDistanciaAOrigen();

        // Mostrar la distancia por pantalla
        System.out.println("La distancia al origen es: " + distancia);
    }
}
```




## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

### Respuesta

El punto de entrada de un programa en Java es el método public static void main(String[] args), que es el primero que ejecuta la máquina virtual cuando se inicia la aplicación. La palabra clave static indica que el método pertenece a la clase y no a un objeto concreto, lo que permite que main se ejecute sin necesidad de crear previamente una instancia.

El modificador static no se utiliza solo en el método main, sino también en atributos y métodos que deben ser compartidos por todas las instancias de una clase. Cuando se combina con final, se emplea para definir constantes, es decir, valores únicos e inmutables como static final double PI = 3.1416;.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

### Respuesta

Para compilar un archivo .java usamos el comando:
javac NombreDelArchivo.java

Por ejemplo, si tienes:
Punto.java

Entonces compilas así:
javac Punto.java

Este comando genera un archivo:
Punto.class

Para compilar un programa en Java desde la línea de comandos se usa el comando javac Nombre.java, que convierte el código fuente en byte‑code y genera un fichero .class, y para ejecutarlo se utiliza java NombreDeLaClase (sin poner .class). Java es un lenguaje híbrido: primero se compila a byte‑code y luego ese byte‑code es ejecutado por la Máquina Virtual de Java (JVM), que actúa como una capa intermedia entre el programa y el sistema operativo. La JVM permite que el mismo programa funcione en cualquier plataforma, y los archivos .class contienen ese byte‑code que la máquina virtual interpreta y optimiza en tiempo de ejecución.



## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

### Respuesta

El operador new crea un objeto en memoria dinámica y devuelve una referencia a él. Funciona como una combinación de creación e inicialización automática del objeto, algo diferente al comportamiento de C.

Un constructor es un método especial cuyo único propósito es inicializar los atributos del objeto. Se ejecuta automáticamente al usar new y tiene el mismo nombre que la clase.

Ejemplo en una clase Empleado:

```java
public class Empleado {

    String dni;
    String nombre;
    String apellidos;

    // Constructor
    public Empleado(String dni, String nombre, String apellidos) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellidos = apellidos;
    }
}
```


## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

### Respuesta

La referencia this señala al objeto actual que ejecuta un método. Se utiliza para diferenciar entre atributos y parámetros con nombres iguales y para acceder de forma clara al estado del objeto.

Aunque muchos lenguajes usan this, como Java o C++, otros como Python emplean self. En lenguajes sin orientación a objetos, como C, este concepto no existe.

```java
public class Punto {

    float x;
    float y;

    // Constructor usando this
    public Punto(float x, float y) {
        this.x = x;  // this.x = atributo, x = parámetro
        this.y = y;
    }

    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }
}

public class Main {
    public static void main(String[] args) {
        Punto p = new Punto(3, 4);
        System.out.println(p.calculaDistanciaAOrigen());
    }
}
```

## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

### Respuesta

```java
public class Main {

    // Clase Punto dentro del mismo archivo
    static class Punto {
        float x;
        float y;

        public Punto(float x, float y) {
            this.x = x;
            this.y = y;
        }

        // Distancia al origen (0,0)
        double calculaDistanciaAOrigen() {
            return Math.sqrt(this.x * this.x + this.y * this.y);
        }

        // NUEVO: distancia entre este punto y otro punto
        double distanciaA(Punto otro) {
            float dx = otro.x - this.x;
            float dy = otro.y - this.y;
            return Math.sqrt(dx * dx + dy * dy);
        }
    }

    public static void main(String[] args) {
        Punto p1 = new Punto(3, 4);
        Punto p2 = new Punto(6, 8);

        System.out.println("Distancia de p1 al origen: " + p1.calculaDistanciaAOrigen()); // 5.0
        System.out.println("Distancia de p1 a p2: " + p1.distanciaA(p2));                 // 5.0
    }
}
```


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

### Respuesta

En Java, los objetos (como Punto) se pasan por valor, pero el valor que se copia es una referencia. Eso significa que dentro del método recibes una copia de la referencia, pero ambas apuntan al mismo objeto en memoria. Por eso, si dentro del método modificas algún atributo del Punto pasado como parámetro, sí afectará al objeto original fuera del método, porque estás trabajando sobre el mismo objeto. 

En cambio, si pasas un tipo primitivo como un int, este sí se pasa por valor real: se copia su contenido, no una referencia, así que si modificas ese entero dentro del método, el cambio no afecta en absoluto al valor original fuera de la función.



## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

### Respuesta

El método toString() en Java es una función heredada de la clase base Object que devuelve una representación en texto del objeto, y se suele sobrescribir para que muestre información útil sobre sus atributos; este concepto existe también en otros lenguajes, como ToString() en C#, toString() en JavaScript o __str__() en Python.

Ejemplo:

```java
public class Main {

    static class Punto {
        float x; // visibilidad por defecto (package-private)
        float y;

        public Punto(float x, float y) {
            this.x = x;
            this.y = y;
        }

        double calculaDistanciaAOrigen() {
            return Math.sqrt(x * x + y * y);
        }

        double distanciaA(Punto otro) {
            float dx = otro.x - this.x;
            float dy = otro.y - this.y;
            return Math.sqrt(dx * dx + dy * dy);
        }

        public String toString() {
            return "Punto(x=" + x + ", y=" + y + ")";
        }
    }

    public static void main(String[] args) {
        Punto p1 = new Punto(3, 4);
        Punto p2 = new Punto(6.5f, 1.2f);

        System.out.println(p1);                
        System.out.println(p2.toString());     
        System.out.println("P1 -> " + p1);      
    }
}
```

## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


### Respuesta

Una clase se parece a un struct de C en el sentido de que ambos agrupan datos bajo un mismo tipo, pero no son equivalentes: al struct le falta lo fundamental que tiene una clase, como la capacidad de incluir métodos, encapsulación, visibilidad (public, private), constructores, herencia, polimorfismo y el hecho de que sus variables se consideren realmente instancias con comportamiento asociado. 

En C, un struct solo contiene datos y no puede tener funciones asociadas ni mecanismos de orientación a objetos, mientras que una clase combina datos y comportamientos formando objetos completos, lo que convierte cada variable de ese tipo en una verdadera instancia con identidad propia.


## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

### Respuesta

Para “emular” en C una clase como Punto con su función para calcular la distancia al origen, usaríamos un struct que solo puede contener datos (por ejemplo, float x; float y;) y definiríamos aparte una función externa que reciba un struct Punto o un puntero a él para realizar el cálculo, ya que en C los struct no pueden incluir métodos. 

La llamada sería algo como distanciaAlOrigen(p) o distanciaAlOrigen(&p), en lugar del estilo orientado a objetos p.calculaDistanciaAOrigen(). En este enfoque, this desaparece, porque en C no existe el concepto de “objeto actual”: es el propio parámetro (el struct o su puntero) el que actúa como “this” de forma manual. En resumen, en C podemos imitar los datos y las funciones, pero no existe un objeto real ni this, ya que el struct no tiene comportamiento asociado.