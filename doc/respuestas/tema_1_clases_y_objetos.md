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
Las cuatro características básicas de la programación orientada a objetos son abstracción, encapsulación, herencia y polimorfismo. Estas características permiten organizar el software de una forma más cercana a la realidad, facilitando la modularidad, la reutilización y el mantenimiento del código.

La abstracción consiste en centrarse en los aspectos relevantes de un objeto e ignorar los detalles innecesarios para el problema que se está resolviendo. Permite definir qué hace un objeto sin preocuparse inicialmente de cómo lo hace, simplificando el diseño y la comprensión del sistema. 

La encapsulación se basa en agrupar datos y operaciones relacionadas dentro de una misma unidad, ocultando el funcionamiento interno y controlando el acceso a la información para evitar usos incorrectos.

La herencia permite crear nuevas clases a partir de otras ya existentes, reutilizando sus características y comportamientos. De este modo, se establece una relación jerárquica entre clases que reduce la duplicación de código y facilita la extensión del sistema. 

El polimorfismo permite que distintos objetos puedan responder de manera diferente ante una misma operación, lo que aporta flexibilidad y hace posible tratar objetos distintos de forma uniforme dentro de un mismo contexto.

## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

### Respuesta
Java, C++, Python, C#

## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

### Respuesta
La programación estructurada es un paradigma que organiza los programas mediante estructuras de control claras, como secuencias, decisiones y bucles, evitando saltos desordenados. Su finalidad es mejorar la legibilidad y facilitar la comprensión y el mantenimiento del código.

Este enfoque permite expresar los algoritmos de forma ordenada, con un flujo de ejecución predecible. Gracias a ello, los programas resultan más fáciles de analizar, depurar y corregir.

La programación modular consiste en dividir un programa en partes independientes llamadas módulos, cada uno encargado de una función concreta. Estos módulos pueden desarrollarse y mantenerse de forma separada, reduciendo la complejidad del sistema y favoreciendo la reutilización del código.

## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

### Respuesta
En programación orientada a objetos, un objeto queda definido por tres elementos fundamentales: identidad, estado y comportamiento. Estos elementos permiten diferenciar un objeto de otro y describir su papel dentro del programa.

La identidad es la característica que distingue a un objeto de los demás, incluso cuando comparte el mismo estado o comportamiento con otros objetos. 

El estado está formado por el conjunto de datos que almacenan la información del objeto en un momento determinado y que puede variar a lo largo de su vida.

El comportamiento describe las acciones que puede realizar un objeto y la forma en que responde a determinadas operaciones. Estas acciones suelen actuar sobre el propio estado del objeto, permitiendo que este interactúe con otros objetos del sistema.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

### Respuesta

Una clase es una descripción o plantilla que define las características y comportamientos que tendrán los objetos de un determinado tipo. En ella se especifican los datos que almacenarán los objetos y las operaciones que podrán realizar, pero por sí sola no representa un elemento concreto del programa.

Una clase no es lo mismo que un objeto. El objeto es una entidad concreta que existe durante la ejecución del programa y que posee valores específicos para sus datos, mientras que la clase es solo el modelo a partir del cual se crean esos objetos. Por tanto, una clase puede dar lugar a múltiples objetos distintos.

Una instancia es cada uno de los objetos creados a partir de una clase. Instanciar una clase significa crear un objeto concreto siguiendo la definición establecida por dicha clase. No todos los lenguajes orientados a objetos manejan obligatoriamente el concepto de clase, ya que algunos se basan en otros mecanismos, aunque mantienen los principios fundamentales de la orientación a objetos.

## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

### Respuesta

Los objetos, en la mayoría de lenguajes orientados a objetos, se almacenan en una zona de memoria dinámica llamada montón o heap. Esta zona permite que los objetos tengan un tiempo de vida independiente del bloque de código donde se crean, lo que resulta esencial para la flexibilidad de la programación orientada a objetos.

La forma exacta en la que se gestionan los objetos no es igual en todos los lenguajes. Algunos lenguajes controlan automáticamente la memoria, mientras que otros requieren que el programador gestione de forma explícita la creación y destrucción de los objetos. Estas diferencias influyen directamente en la seguridad y complejidad del manejo de la memoria.

La recolección de basura es un mecanismo automático que se encarga de liberar la memoria ocupada por objetos que ya no son accesibles ni necesarios para el programa. Su objetivo es evitar fugas de memoria y simplificar el trabajo del programador, delegando la gestión de la liberación de memoria al propio sistema de ejecución del lenguaje.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

### Respuesta
Un método es una operación asociada a una clase u objeto que define un comportamiento concreto. Representa una acción que puede realizar un objeto y, normalmente, actúa sobre los datos que forman parte de su estado, permitiendo manipularlos o consultarlos de forma controlada.

Los métodos permiten organizar la funcionalidad del programa, separando claramente qué acciones están disponibles y cómo se interactúa con los objetos. De este modo, se mejora la claridad del diseño y se refuerza la encapsulación, al acceder a los datos únicamente a través de operaciones definidas.

La sobrecarga de métodos consiste en definir varios métodos con el mismo nombre dentro de una misma clase, pero con distinta lista de parámetros. Esto permite utilizar una misma operación conceptual adaptada a diferentes situaciones, facilitando la legibilidad del código y aportando flexibilidad al diseño.

## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

### Respuesta

Una clase en Java define la estructura y el comportamiento de los objetos. En este caso, la clase Punto representa un punto en el plano mediante dos atributos que almacenan sus coordenadas y un método que calcula una operación asociada a esos datos.

Los atributos tienen visibilidad por defecto, lo que permite su acceso dentro del mismo paquete. El método definido calcula la distancia del punto al origen de coordenadas aplicando la fórmula matemática correspondiente.

class Punto {
    double x;
    double y;

    double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
}

Ejemplo básico de uso de la clase mediante la creación de una instancia y la llamada a un método:
class PruebaPunto {
    public static void main(String[] args) {
        Punto p = new Punto();
        p.x = 3;
        p.y = 4;

        double d = p.calculaDistanciaAOrigen();
        System.out.println(d);
    }
}




## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

### Respuesta
El punto de entrada de un programa en Java es el método main. Este método es el primero que se ejecuta cuando se lanza una aplicación y debe tener una forma concreta para que la máquina virtual pueda localizarlo correctamente.

La palabra clave static indica que un método o atributo pertenece a la clase y no a los objetos creados a partir de ella. En el caso de main, se utiliza porque el programa debe poder comenzar sin necesidad de crear previamente ningún objeto.

static no se emplea únicamente en el método main, ya que puede usarse en otros métodos y atributos cuando se desea que sean comunes a toda la clase. Cuando se combina con final, se indica que el valor o comportamiento no puede modificarse, lo que se utiliza para definir constantes o impedir redefiniciones.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

### Respuesta
Para compilar un programa Java desde la línea de comandos se utiliza el compilador javac, indicando el archivo fuente. Para ejecutar el programa, se emplea el comando java seguido del nombre de la clase que contiene el método main.

Java es un lenguaje compilado, pero no directamente a código máquina. El compilador genera un código intermedio que puede ejecutarse en distintas plataformas, lo que aporta portabilidad.

La máquina virtual de Java es un entorno de ejecución que interpreta ese código intermedio y lo ejecuta en el sistema. El byte-code es ese código intermedio generado por el compilador y se almacena en ficheros con extensión .class, que son los que realmente se ejecutan.


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

### Respuesta

La palabra clave new se utiliza para crear un objeto a partir de una clase, reservando memoria para él y devolviendo una referencia al mismo. Es el mecanismo fundamental para instanciar objetos en Java.

Un constructor es un método especial que se ejecuta automáticamente al crear un objeto. Su finalidad es inicializar el estado del objeto, asignando valores iniciales a sus atributos.

Ejemplo de un constructor en una clase Empleado con varios atributos:

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



## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

### Respuesta
La referencia this se utiliza dentro de una clase para hacer referencia al propio objeto que está ejecutando el método. Permite distinguir entre los atributos del objeto y otros elementos con el mismo nombre, como los parámetros de un método o constructor.

No en todos los lenguajes orientados a objetos se llama igual, aunque el concepto es equivalente. Cada lenguaje adopta su propia palabra clave para referirse al objeto actual.

Ejemplo de uso de this en la clase Punto:
class Punto {
    double x;
    double y;

    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }
}



## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

### Respuesta
Se puede añadir a la clase Punto un método que calcule la distancia entre el propio objeto (this) y otro punto recibido como parámetro. Este método representa una operación entre dos objetos del mismo tipo.

El cálculo se basa en la diferencia entre las coordenadas de ambos puntos y aplica la fórmula habitual de la distancia euclídea. El uso de this permite acceder explícitamente a los atributos del objeto que invoca el método.
double distanciaA(Punto otro) {
    double dx = this.x - otro.x;
    double dy = this.y - otro.y;
    return Math.sqrt(dx * dx + dy * dy);
}



## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

### Respuesta
En Java, los objetos se pasan por valor, pero el valor que se copia es la referencia al objeto. Esto significa que, si se modifica el estado del objeto dentro del método, los cambios sí afectan al objeto original fuera del método.

Por tanto, al pasar un Punto como parámetro, ambos nombres hacen referencia al mismo objeto en memoria. No se crea una copia del objeto, sino una copia de la referencia.

En cambio, los tipos primitivos como int se pasan por copia directa del valor. Si un entero se modifica dentro de un método, ese cambio no afecta a la variable original fuera del método.


## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

### Respuesta
El método toString() se utiliza para obtener una representación en forma de texto de un objeto. En Java, este método está definido en la clase base de la que heredan todos los objetos y puede redefinirse para mostrar información significativa.

Este concepto existe también en otros lenguajes orientados a objetos, aunque con distintos nombres o mecanismos, y cumple la misma función de convertir un objeto en una cadena legible.

Ejemplo de toString() en la clase Punto:

@Override
public String toString() {
    return "Punto(" + x + ", " + y + ")";
}



## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?

### Respuesta

Una clase es conceptualmente similar a un struct en C en cuanto a que ambos agrupan datos relacionados bajo un mismo nombre. En ese sentido, una clase puede verse como una evolución del struct.

Sin embargo, al struct le faltan aspectos clave como los métodos asociados directamente a los datos, el control de acceso, los constructores y el soporte directo para conceptos como herencia o polimorfismo.

Además, las variables de tipo struct no tienen comportamiento propio, mientras que los objetos creados a partir de una clase combinan datos y operaciones, lo que permite hablar de instancias con identidad y comportamiento.



## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

### Respuesta

En C se puede emular una clase utilizando un struct para los datos y funciones externas que operen sobre él. La función que calcula la distancia al origen recibe explícitamente el struct como parámetro.

#include <math.h>
struct Punto {
    double x;
    double y;
};
double distanciaAOrigen(struct Punto p) {
    return sqrt(p.x * p.x + p.y * p.y);
}


En este enfoque, this desaparece como referencia implícita. Su papel lo asume el parámetro de la función, que representa de forma explícita el objeto sobre el que se quiere operar, lo que hace más manual la gestión pero conceptualmente equivalente.