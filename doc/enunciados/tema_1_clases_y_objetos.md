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
La abstracción permite trabajar con ideas más simples, ignorando detalles que no son necesarios en ese momento. De esta forma, se facilita la comprensión de problemas complejos sin necesidad de conocer su funcionamiento interno, el resto de características también colaboran en esto.
La segunda característica es la encapsulación, que se refiere a la capacidad de ocultar los datos de un objeto y permitir el acceso únicamente a través de métodos específicos. Esto evita que el estado interno del objeto pueda modificarse de forma incorrecta desde otras partes del programa. En la práctica, esta idea ayuda a mantener el código más seguro y controlado.
La herencia es otra característica importante. Esta permite que una clase pueda basarse en otra ya existente, reutilizando su estructura y comportamiento. Gracias a esto, se pueden crear jerarquías de clases donde las más generales sirven como base para otras más específicas. Esta propiedad reduce la repetición de código y facilita la extensión de programas grandes sin tener que reescribir funcionalidades.
Por último, el polimorfismo permite que diferentes clases respondan de manera distinta a un mismo método. Esto significa que se puede llamar a una misma función, pero la acción concreta que realiza depende del tipo real del objeto. Esta propiedad aporta mucha flexibilidad al programa, ya que permite tratar a distintos objetos de forma uniforme, dejando que cada uno actúe según su naturaleza.



## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

### Respuesta
Existen varios lenguajes populares que permiten programar orientado a objetos. Uno muy conocido es Java, que fue diseñado desde el principio para trabajar únicamente con clases y objetos, lo que facilita aprender este paradigma desde cero. 
También se encuentra C++, que añade orientación a objetos encima del lenguaje C y permite usar clases, herencia y polimorfismo, por lo que resulta familiar para quien viene de C tradicional.
Además, Python es un lenguaje muy extendido donde prácticamente todo funciona como un objeto, lo que simplifica entender este modelo sin complicaciones técnicas. 
Por último, C# es otro lenguaje muy utilizado, especialmente en entornos Windows, y aplica la orientación a objetos de forma clara y estructurada. Estos cuatro lenguajes son ejemplos representativos modernos de programación orientada a objetos.
Java, C#, ¿Rust?, y C++: compiladas, un proceso que el programador es consciente y detecta errores a la vez que traduce el código a una versión de bajo nivel ejecutable.


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

### Respuesta
Antes de la programación orientada a objetos, uno de los paradigmas más utilizados era la programación estructurada. Este estilo se basa en dividir un programa en bloques de instrucciones que se ejecutan de forma ordenada, utilizando estructuras como if, while, for y funciones simples. El objetivo principal es evitar el uso excesivo de saltos como goto, que hacían el código difícil de seguir. La programación estructurada busca que el flujo de un programa sea claro, predecible y fácil de entender, además de que suprime el salto arbitrario.
Un paso más allá dentro de este enfoque es la programación modular, que consiste en dividir un programa en módulos o partes independientes. Cada módulo tiene una función concreta y se comunica con los demás mediante interfaces bien definidas. Este método mejora la organización del programa, facilita la reutilización de código y permite que diferentes partes del proyecto se desarrollen y mantengan por separado, reduciendo errores y aumentando la claridad general del sistema.

## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

### Respuesta
En programación orientada a objetos, un objeto se define por tres elementos fundamentales. El primero son los atributos, que representan las características o datos que describen al objeto. Por ejemplo, si se piensa en un objeto que representa a una persona, los atributos podrían ser el nombre, la edad o la altura. Estos valores permiten diferenciar un objeto de otro dentro de un mismo programa.
El segundo elemento son los métodos, que representan las acciones o comportamientos que un objeto puede realizar. Siguiendo el ejemplo anterior, una persona podría tener métodos como caminar, hablar o cumplir años. 
Finalmente, todo objeto tiene una identidad, que permite distinguirlo de otros incluso si comparten exactamente los mismos atributos. Esta identidad asegura que cada objeto sea una entidad independiente dentro de la ejecución del programa. Hay que verlo como que cada objeto tiene una dirección en memoria.


## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

### Respuesta
Una clase es un modelo que describe qué atributos y métodos tendrán los objetos. Funciona como un plano o plantilla que define la estructura y el comportamiento común de un conjunto de elementos. Por sí misma no almacena datos reales, solo la definición.
Un objeto no es lo mismo que una clase. Un objeto es una instancia de esa clase, es decir, un ejemplar concreto creado a partir de ella. Cada instancia tiene valores propios en sus atributos y puede ejecutar las acciones definidas por la clase.
Aunque muchos lenguajes orientados a objetos usan clases (como Java, C++ o C#), no todos dependen de ellas. Algunos, como JavaScript, utilizan un modelo basado en prototipos, donde los objetos pueden crearse sin necesidad de una clase formal.

## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

### Respuesta
Los objetos suelen almacenarse en la heap, una zona de memoria usada para datos creados dinámicamente durante la ejecución. En lenguajes como Java o Python, los objetos siempre se guardan ahí. En cambio, en C++ pueden estar en la pila (stack) o en la heap, dependiendo de cómo se creen.
No todos los lenguajes gestionan la memoria igual. Algunos la administran automáticamente, mientras que otros requieren que el programador la gestione manualmente. Esto hace que el comportamiento exacto pueda variar entre lenguajes.
La recolección de basura es un sistema automático que libera la memoria de los objetos que ya no se usan. Lenguajes como Java, Python o C# la incluyen para evitar fugas de memoria y simplificar el manejo de objetos.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

### Respuesta
Un método es una acción o comportamiento asociado a una clase u objeto. Define lo que un objeto puede hacer, como calcular un valor, modificar un atributo o mostrar información. En lenguajes orientados a objetos, los métodos permiten que los objetos interactúen entre sí y realicen operaciones concretas.
La sobrecarga de métodos consiste en definir varios métodos con el mismo nombre dentro de una misma clase, pero con parámetros diferentes. Esto permite utilizar un mismo nombre para acciones relacionadas, dejando que el lenguaje seleccione automáticamente cuál usar según los argumentos que reciba. Gracias a esto, el código resulta más claro y flexible.


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

### Respuesta
    class Punto {
        double x;   // visibilidad por defecto
        double y;

        double calculaDistanciaAOrigen() {
            return Math.sqrt(x * x + y * y);
        }
    }

    public class Main {
        public static void main(String[] args) {
            Punto p = new Punto();
            p.x = 3;
            p.y = 4;

            double d = p.calculaDistanciaAOrigen();
            System.out.println("Distancia al origen: " + d);  // Imprime 5.0
        }
    }


## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

### Respuesta
En Java, el punto de entrada de un programa es el método main. Este método es el primero que ejecuta la máquina virtual de Java cuando se inicia un programa, y su forma estándar es: public static void main(String[] args). Sin este método, un programa normal escrito en Java no puede iniciarse.
La palabra static indica que el método pertenece a la clase y no a un objeto concreto. Gracias a esto, la máquina virtual puede ejecutar main sin necesidad de crear una instancia previa de la clase. El uso de static no se limita al método main; también puede aplicarse a atributos o métodos que deben ser accesibles sin crear objetos, como constantes o funciones auxiliares.
Combinar static con final sirve normalmente para declarar constantes, es decir, valores que no cambian durante la ejecución del programa. Por ejemplo, static final double PI = 3.14159; define una constante accesible desde la clase sin necesidad de instanciarla y cuyo valor no puede modificarse. Esta combinación es habitual cuando se desea un valor único, fijo y compartido por todos los objetos de la clase.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

### Respuesta
Para compilar un programa en Java desde la línea de comandos se utiliza el comando javac, que genera los ficheros compilados. Por ejemplo, si se tiene un archivo Main.java, se compila con javac Main.java
Esto produce un archivo Main.class. Para ejecutarlo se usa el comando java, escribiendo el nombre de la clase sin la extensión java Main
Aunque Java necesita una compilación previa, no genera un ejecutable directamente como ocurre en C o C++. Java es considerado un lenguaje compilado y también interpretado, porque el código primero se compila a un formato intermedio llamado bytecode, y después este bytecode es interpretado o ejecutado por la máquina virtual de Java (JVM).
La máquina virtual es un programa que actúa como intermediario entre el código Java y el sistema operativo. Su función es ejecutar el bytecode de forma segura y portable. Gracias a esto, un mismo programa Java puede ejecutarse en Windows, Linux o macOS, siempre que exista una JVM disponible para esa plataforma.
El bytecode es un conjunto de instrucciones independientes del sistema operativo que se almacenan en los ficheros .class. Estos ficheros no son código máquina real, sino un formato intermedio que la JVM sabe interpretar. Este enfoque permite que Java sea portable entre plataformas y facilita mecanismos como la recolección de basura y la ejecución controlada.


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos
    

### Respuesta
    class Empleado {
            String dni;
            String nombre;
            String apellidos;

            Empleado(String dni, String nombre, String apellidos) {
                this.dni = dni;
                this.nombre = nombre;
                this.apellidos = apellidos;
            }
        }

        Ejemplo de uso:
        Empleado e = new Empleado("12345678A", "Ana", "Pérez Gómez");


## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

### Respuesta
La referencia this es un identificador especial que apunta al objeto actual dentro de los métodos de una clase. Se utiliza para acceder a los atributos y métodos de esa misma instancia, y también para desambiguar cuando un parámetro del método tiene el mismo nombre que un atributo de la clase. En constructores, this permite inicializar los campos de la instancia con los valores recibidos.
No se llama igual en todos los lenguajes. En Java, C++ y JavaScript se utiliza this, mientras que en Python se emplea el nombre de parámetro convencional self (no es palabra reservada, pero se usa por convención). Aun así, la idea es la misma: referirse al objeto sobre el que se está trabajando.
class Punto {
    double x;
    double y;

    // Constructor: desambiguación con 'this'
    Punto(double x, double y) {
        this.x = x;  // 'this.x' es el atributo; 'x' es el parámetro
        this.y = y;
    }

    // Método que usa 'this' para llamar a otro método y acceder a atributos
    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }

    // Setter con validación, usando 'this' para dejar claro que se asigna al campo
    void mover(double x, double y) {
        this.x = x;
        this.y = y;
    }
}



## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

### Respuesta
    class Punto {
        double x;
        double y;

        Punto() {}

        Punto(double x, double y) {
            this.x = x;
            this.y = y;
        }

        double calculaDistanciaAOrigen() {
            return Math.sqrt(this.x * this.x + this.y * this.y);
        }

        // Nuevo método: distancia entre this y otro Punto
            double distanciaA(Punto q) {
            double dx = this.x - q.x;
            double dy = this.y - q.y;
            return Math.sqrt(dx * dx + dy * dy);
        }
    }

## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

### Respuesta
En Java, cuando se pasa un objeto como parámetro —como ocurre con un Punto— lo que se pasa no es una copia completa del objeto, sino una copia de la referencia que apunta a él. Esto significa que ambos, el parámetro del método y el objeto original, apuntan a la misma zona de memoria. Por tanto, si dentro del método se modifica algún atributo del objeto recibido, esos cambios sí afectan al objeto fuera del método.
Sin embargo, este comportamiento no es igual para los tipos primitivos, como int. Cuando un valor primitivo se pasa como parámetro, Java realiza una copia del valor, por lo que cualquier modificación dentro del método afecta solamente a esa copia local. El valor original fuera del método permanece sin cambios. Este comportamiento corresponde a lo que se conoce como paso por valor, aunque en el caso de los objetos ese valor sea una referencia.


## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

### Respuesta
En Java, toString() es un método heredado de Object que devuelve una representación en texto del objeto. Se suele sobrescribir para que muestre información útil de los atributos, en lugar del formato por defecto (nombre de clase + hash). Esta representación resulta práctica para depuración, logs y mensajes al usuario.
Existen métodos equivalentes en otros lenguajes. En Python se emplea __str__ (y __repr__), en C# también se usa ToString(), y en JavaScript los objetos pueden definir toString() personalizado. La idea común es proporcionar una forma legible de mostrar el contenido del objeto.

class Punto {
    double x;
    double y;

    Punto() {}

    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    // Sobrescritura de toString para representación legible
    @Override
    public String toString() {
        return "Punto(x=" + x + ", y=" + y + ")";
    }
}

public class Main {
    public static void main(String[] args) {
        Punto p = new Punto(3, 4);
        System.out.println(p);            // Usa implícitamente p.toString()
        System.out.println(p.toString()); // Imprime: Punto(x=3.0, y=4.0)
    }
}

## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


### Respuesta
En C, un struct permite agrupar datos, pero no incluye comportamiento. En una clase, además de atributos, pueden definirse métodos, constructores, control de visibilidad y otras características propias de la programación orientada a objetos. Por tanto, una clase combina datos y funciones relacionadas dentro de la misma unidad, mientras que un struct tradicional únicamente almacena información.
Para que un struct se comportase como una clase sería necesario que incorporase mecanismos que C no ofrece: métodos asociados, encapsulación mediante modificadores de acceso, constructores, destructores y soporte para conceptos como herencia o polimorfismo. Sin estos elementos, las variables creadas a partir de un struct no se consideran instancias en el sentido de la orientación a objetos, sino únicamente bloques de memoria que contienen datos.


## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

### Respuesta
