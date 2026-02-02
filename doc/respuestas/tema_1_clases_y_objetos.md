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

Las cuatro características básicas que suelen citarse en POO son **abstracción**, **encapsulación**, **herencia** y **polimorfismo**.
- La **abstracción** consiste en modelar un concepto del mundo real quedándose con lo esencial para el problema y ocultando el resto; se define qué hace algo sin tener que entrar en todos los detalles internos de cómo lo hace. 
  - Olvidar detalles para manejar temas complejos y facilitar el mantenimiento del codigo.
- La **encapsulación** agrupa **datos** y **operaciones** relacionadas en una unidad (la clase/objeto) y controla el acceso a esos datos, de forma que el estado interno se manipule de manera segura mediante métodos. 
- La **herencia** permite definir una clase nueva a partir de otra existente, reutilizando y extendiendo comportamiento (relación “es-un” en muchos casos). Crear jerarquias.
- El **polimorfismo** el mismo metodo con el mismo nombre haciendo que una misma operación se comporte de manera distinta según el objeto concreto.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

Entre los lenguajes populares que soportan POO están Java, C++, C# y Python. En todos ellos se pueden definir tipos compuestos con atributos y métodos, crear instancias (objetos) y organizar el código alrededor de esas entidades.

Aun así, el “grado” de orientación a objetos varía: por ejemplo, en Java casi todo gira alrededor de clases y objetos, mientras que C++ permite mezclar estilos (procedimental, genérico y orientado a objetos). Python también permite programar de forma orientada a objetos, aunque es flexible y no obliga a usar ese paradigma para todo.


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

La programación estructurada es un paradigma que propone construir programas mediante estructuras de control claras y bien definidas (secuencia, selección e iteración) evitando el salto incontrolado con ``goto``. La idea es que el flujo del programa sea legible, verificable y fácil de razonar, descomponiendo problemas en partes y usando funciones para organizar.

La programación modular da un paso más en organización: se divide el programa en módulos con responsabilidades concretas, separando interfaz y detalles internos. Un módulo expone “qué ofrece” (funciones, tipos, constantes) y oculta “cómo lo implementa”, lo que facilita reutilización, mantenimiento y trabajo en equipo. En C, por ejemplo, esto se refleja en pares ``.h`` (interfaz) y ``.c`` (implementación).

## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

Un objeto suele definirse por identidad, estado y comportamiento. La identidad es lo que lo hace “ese objeto” concreto, distinto de otros aunque tengan los mismos valores; en muchos lenguajes se asocia a su existencia como entidad en memoria.

El estado son los datos que guarda (sus atributos o campos), que pueden cambiar a lo largo del tiempo. El comportamiento son las operaciones que puede realizar o que se pueden realizar sobre él (sus métodos), normalmente actuando sobre su propio estado o interactuando con otros objetos.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

Una clase es un “molde” o definición: describe qué atributos y métodos tendrán los objetos de ese tipo. Un objeto es una entidad concreta creada siguiendo esa definición, con su propio estado. Por tanto, clase y objeto no son lo mismo: la clase es la descripción; el objeto es el resultado creado a partir de esa descripción.

Una instancia es precisamente un objeto creado a partir de una clase: “instancia de la clase X”. No todos los lenguajes orientados a objetos se basan en clases; existen lenguajes orientados a objetos basados en prototipos (por ejemplo, JavaScript), donde los objetos pueden derivar de otros objetos sin una clase “molde” tradicional.


## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

El lugar “exacto” donde se almacenan los objetos depende del lenguaje y del modelo de memoria. En Java, los objetos creados con ``new`` se almacenan en el heap (memoria dinámica), y las variables que los manejan suelen ser referencias (algo parecido a un puntero, pero sin aritmética de punteros). En C++ puede haber objetos en stack, heap o embebidos dentro de otros objetos, según cómo se declaren.

No es igual en todos los lenguajes, porque cada uno define reglas diferentes para creación, vida útil y liberación. La recolección de basura (garbage collection) es un mecanismo (típico de Java, C#, etc.) por el cual el entorno de ejecución detecta automáticamente objetos que ya no son accesibles desde el programa y libera su memoria, evitando que se tenga que llamar manualmente a ``free``/``delete``.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

Un método es una función asociada a una clase/objeto, que normalmente opera sobre el estado del objeto. Desde una perspectiva de C/C++, puede verse como una función que “pertenece” a un tipo y que, en métodos de instancia, recibe implícitamente una referencia al objeto sobre el que se invoca (en Java se accede mediante ``this``).

La sobrecarga de métodos consiste en definir varios métodos con el mismo nombre dentro de una clase, pero con distinta lista de parámetros (número o tipos). El compilador decide cuál se llama según los argumentos usados en la invocación. En Java, la sobrecarga no se basa en el tipo de retorno, sino en la firma de parámetros.


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

Se puede definir una clase ``Punto`` con dos atributos ``x`` e ``y`` y un método que calcule la distancia al origen aplicando Pitágoras: 
$\sqrt{x^2+y^2}$. La visibilidad “por defecto” en Java (sin ``public/private/protected``) es package-pvivate, es decir, accesible dentro del mismo paquete.

A continuación se muestra una implementación mínima y un ejemplo de uso creando una instancia y llamando al método:
```java
public class Punto {
    double x;
    double y;
    double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    public static void main(String[] args) {
        Punto p = new Punto();
        p.x = 3;
        p.y = 4;
        System.out.println(p.calculaDistanciaAOrigen()); // 5.0
    }
}
```

## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

El punto de entrada típico en Java es el método ``public static void main(String[] args)``, que es el que la JVM busca para arrancar la ejecución de una aplicación. Se define dentro de alguna clase y, al empezar, todavía no existe ningún objeto “principal” creado automáticamente, así que se necesita un método invocable sin instancia.

``static`` indica que el método o atributo pertenece a la clase, no a un objeto concreto. No se usa solo en ``main``: también se usa para constantes de clase, funciones de utilidad (por ejemplo, ``Math.sqrt``) o contadores compartidos por todas las instancias. Cuando se combina con ``final``, normalmente se busca declarar constantes: ``static final`` significa “un único valor compartido por la clase y que no puede cambiar”.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

Para compilar y ejecutar desde línea de comandos se suele hacer: primero ``javac`` para compilar el ``.java`` y luego ``java`` para ejecutar la clase compilada. Por ejemplo, si el archivo se llama ``Punto.java`` y contiene una clase ``Punto`` con ``main``, se haría:
```java
javac Punto.java
java Punto
```
Java se considera compilado y ejecutado sobre una máquina virtual. ``javac`` no produce código máquina nativo, sino bytecode, que se guarda en ficheros ``.class``. Ese bytecode lo ejecuta la JVM (Máquina Virtual de Java), que actúa como una capa intermedia: permite portabilidad (mismo ``.class`` en distintos sistemas) y además puede aplicar optimizaciones en tiempo de ejecución (por ejemplo, mediante JIT).


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

``new`` es el operador que **crea un objeto** en memoria (en Java, en el hea y devuelve una **referencia** a ese objeto. En ese proceso se invoca un constructor, que es un bloque especial que inicializa el objeto y tiene el mismo nombre que la clase, sin tipo de retorno. Si no se define ninguno, Java puede aportar un **constructor** por defecto (vacío) en ciertas condiciones.

Un ejemplo de clase ``Empleado`` con un constructor que inicializa ``dni``, ``nombre`` y ``apellidos`` sería:

```java
public class Empleado {
    String dni;
    String nombre;
    String apellidos;

    Empleado(String dni, String nombre, String apellidos) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellidos = apellidos;
    }
}
```

## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

``this`` es una referencia al objeto actual, es decir, a la instancia sobre la que se está ejecutando el método. Se usa para acceder explícitamente a atributos/métodos del propio objeto y para resolver ambigüedades cuando un parámetro tiene el mismo nombre que un atributo. En C++ existe un concepto equivalente llamado ``this``, pero en otros lenguajes puede tener nombres distintos (por ejemplo, self en Python).

Un ejemplo típico en ``Punto`` es usar ``this`` para diferenciar atributos de parámetros:
```java
public class Punto {
    double x;
    double y;

    void set(double x, double y) {
        this.x = x;
        this.y = y;
    }
}
```

## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

Para calcular la distancia entre dos puntos se aplica de nuevo Pitágoras sobre las diferencias: 
$\sqrt{(x_2−x_1)^2+(y_2−y_1)^2}$. En un método de instancia, this representa el punto “origen” del cálculo, y el parámetro representa el punto “destino”.

Un ejemplo de método ``distanciaA`` dentro de ``Punto`` sería:
```java
double distanciaA(Punto otro) {
    double dx = otro.x - this.x;
    double dy = otro.y - this.y;
    return Math.sqrt(dx * dx + dy * dy);
}
```


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

En Java, los parámetros se pasan **siempre por valor**, pero hay un matiz clave: cuando se pasa un objeto, lo que se pasa “por valor” es la **referencia** al objeto. Eso implica que dentro del método se puede modificar el estado del objeto (sus atributos) y esos cambios se verán fuera, porque se está apuntando al mismo objeto. En cambio, si dentro del método se reasigna el parámetro para que apunte a otro objeto, esa reasignación no afecta al exterior.

Con tipos primitivos como ``int``, el valor copiado es el número en sí. Si se modifica el ``int`` dentro del método, el cambio no sale fuera porque se está modificando una copia local. Esta diferencia es importante al venir de C/C++, porque en Java no se pasa “la variable” por referencia al estilo de ``int&``, ni se usan punteros para elegir ese comportamiento.


## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

``toString()`` es un método que define una representación textual del objeto. En Java se usa muchísimo para depuración, logs y salida por pantalla: cuando se imprime un objeto, Java acaba llamando a ``toString()`` para obtener una cadena. Todas las clases heredan una versión básica desde ``Object``, y se suele sobrescribir para que sea informativa.

La idea existe en otros lenguajes con nombres parecidos o equivalentes (por ejemplo, ``__str__`` en Python). Un ejemplo en ``Punto`` sería:
```java
@Override
public String toString() {
    return "Punto{x=" + x + ", y=" + y + "}";
}
```


## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


Un ``struct`` en C se parece a una clase en el sentido de que permite agrupar datos bajo un mismo tipo. Sin embargo, en C el ``struct`` no integra de forma nativa el comportamiento asociado (métodos) ni mecanismos típicos de la POO como encapsulación formal (visibilidades), herencia o polimorfismo.

Para que un ``struct`` “se comporte” como una clase, se necesita añadir disciplina o convenciones: funciones que operen sobre ese ``struct``, pasar explícitamente el puntero al ``struct`` como primer parámetro (simulando ``this``), y organizar el código para que la “interfaz” y la “implementación” estén claras. Aun así, faltan características del lenguaje que hagan cumplir esas reglas automáticamente.

## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

Se puede emular definiendo un ``struct Punto`` con ``x`` e ``y`` y una función ``distanciaAlOrigen`` que reciba un puntero (o la estructura por valor). Lo que en Java sería ``this``, en C se vuelve **un parámetro explícito** (por convención suele llamarse ``p`` o ``self``), porque el lenguaje no tiene métodos asociados al tipo.

Un ejemplo mínimo en C sería:

```c
#include <math.h>

typedef struct {
    double x;
    double y;
} Punto;

double distanciaAlOrigen(const Punto* self) {
    return sqrt(self->x * self->x + self->y * self->y);
}

/* uso */
#include <stdio.h>
int main(void) {
    Punto p = {3, 4};
    printf("%f\n", distanciaAlOrigen(&p)); /* 5.000000 */
    return 0;
}
```
Aquí ``self`` cumple el papel de ``this``: es la “referencia” al objeto sobre el que se opera, pero en C debe pasarse manualmente y no existe sintaxis de método como ``p.calculaDistanciaAOrigen()``.