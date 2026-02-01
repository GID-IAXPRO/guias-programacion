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

### Respuesta:
As catro características básicas da programación orientada a obxectos son encapsulamento, abstracción, herdanza e polimorfismo. O encapsulamento consiste en agrupar nunha mesma clase os datos e os métodos que operan sobre eles, ocultando ao exterior os detalles internos. Isto permítese mediante modificadores de acceso como private ou public, garantindo que o estado interno só poida modificarse de maneira controlada a través de métodos ben definidos. Deste modo lógrase unha maior seguridade e un control máis claro sobre como se manipulan os datos.
A abstracción refírese a representar conceptos complexos de forma simplificada, mostrando só aquilo que é esencial. Nunha clase, isto conséguese definindo métodos que expresan o comportamento relevante sen obrigar ao usuario a coñecer os detalles internos da implementación. Esta idea permite traballar pensando nos “que fan” os obxectos, e non en “como o fan”, facilitando o deseño e a reutilización de compoñentes.
A herdanza permite crear novas clases a partir doutras xa existentes, reutilizando código e ampliando funcionalidades. Mediante esta técnica, unha clase derivada herda os campos e métodos da clase base, podendo engadir novos comportamentos ou redefinir algúns dos existentes. Isto resulta útil para modelar relacións do tipo “é un”, como que un Coche é un tipo de Vehiculo.
Por último, o polimorfismo permite que un mesmo método ou referencia se comporte de maneira diferente segundo o tipo concreto do obxecto co que se traballa. En Java isto maniféstase principalmente a través da redefinición de métodos (override) e do uso de referencias de clase base que apuntan a obxectos de clases derivadas. O resultado é unha maior flexibilidade, xa que diferentes obxectos poden responder á mesma operación de forma adaptada ás súas características.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

### Respuesta:
Algúns dos linguaxes máis populares que permiten a programación orientada a obxectos son Java, C++, Python e C#. Todos eles permiten crear clases, obxectos e aplicar conceptos básicos como herdanza ou polimorfismo, aínda que cada un o fai co seu propio estilo e nivel de rigor.
Estes catro linguaxes son amplamente utilizados na industria e no ensino, polo que adoitan considerarse exemplos representativos cando se fala de POO. A súa popularidade débese tanto á súa versatilidade como á facilidade para aplicar neles os principios fundamentais deste paradigma.


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

### Respuesta:
A programación estruturada é un paradigma baseado na idea de dividir un programa en bloques lógicos que se executan seguindo un fluxo claro e controlado. Este enfoque evita instrucións como goto e baséase en tres estruturas fundamentais: secuencia, selección (if/else) e repetición (bucles). A súa intención é que o código sexa máis lexible, entendible e fácil de depurar, reducindo a complexidade asociada aos saltos incontrolados que existían na programación máis antiga.
A programación modular pode considerarse unha evolución natural da estruturada, xa que organiza o programa en partes máis pequenas chamadas módulos ou funcións. Cada módulo trata unha responsabilidade concreta e pode desenvolverse, probarse e modificarse de maneira independente. Isto permite mellorar a mantenibilidade do código, facilita a reutilización e axuda a que varios programadores poidan traballar ao mesmo tempo nun mesmo proxecto sen interferencias constantes.
En resumo, a programación estruturada proporciona unha forma ordeada de controlar o fluxo dun programa, mentres que a programación modular engade un nivel superior de organización, agrupando funcionalidades en unidades ben definidas. Ambos paradigmas serviron como base conceptual antes da chegada da programación orientada a obxectos, que introduce novas formas de organizar tanto os datos como os comportamentos.


## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

### Respuesta:
Un obxecto en programación orientada a obxectos defínese a partir de tres elementos fundamentais: estado, comportamento e identidade. O estado representa a información que o obxecto almacena, é dicir, os valores das súas variables internas. Cada obxecto conserva o seu propio estado, polo que dous obxectos da mesma clase poden ter valores distintos nos seus atributos.
O comportamento refírese ás accións que o obxecto pode realizar, e exprésase a través dos seus métodos. Estes métodos permiten modificar o estado interno, interactuar con outros obxectos ou realizar cálculos, definindo así como responde o obxecto ante determinadas operacións. Grazas ao comportamento, un obxecto non é só un conxunto de datos, senón unha entidade activa.
Por último, a identidade distingue un obxecto doutro, incluso se teñen o mesmo estado e comportamento. En Java, esta identidade está asociada ao espazo de memoria que ocupa o obxecto cando é creado con new. Esta característica garante que dúas instancias aparentemente iguais sigan sendo obxectos diferentes con existencia propia dentro do programa.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

### Respuesta:
Unha clase é unha estrutura que describe un tipo de obxecto, definindo que datos terá (atributos) e que operacións poderá realizar (métodos). Pode entenderse como un molde ou plantilla a partir da cal se crean obxectos reais. Por tanto, unha clase non é un obxecto, senón a definición teórica que permite xerar obxectos cun estado e comportamento concretos.
Un obxecto, pola contra, é unha entidade concreta creada a partir dunha clase. Cada obxecto ten o seu propio estado, distinto do doutros obxectos aínda que procedan da mesma clase. A creación dun obxecto denomínase instanciación, e o resultado desa operación recibe o nome de instancia. Así, unha instancia é simplemente un obxecto específico que existe na memoria e que foi construído seguindo o deseño establecido pola clase correspondente.
Non todos os linguaxes orientados a obxectos usan o concepto de clase da mesma maneira, nin sequera todos o empregan. Linguaxes como Java, C++, C# ou Python permiten definir clases explícitas, pero existen outros como JavaScript que tradicionalmente se basearon en prototipos, permitindo orientación a obxectos sen necesidade de clases formais (aínda que posteriormente incorporaron sintaxe de clases por comodidade). Isto mostra que a orientación a obxectos é un paradigma amplo, no que o uso de clases é frecuente pero non obrigatorio.


## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

### Respuesta:
En Java, os obxectos almacénanse na memoria dinámica, é dicir, no montón (heap). Cada vez que se utiliza new, resérvase espazo no heap para gardar o estado dese obxecto. Mentres tanto, as variables que apuntan a eses obxectos adoitan situarse na pila (stack), pero só gardan a referencia, non o contido do obxecto. Este modelo permite que diferentes partes do programa compartan un mesmo obxecto simplemente copiando a referencia.
A forma de almacenar obxectos non é igual en todos os linguaxes. En C++, por exemplo, un obxecto pode estar na pila, no heap ou incluso ser global, dependendo de como se declare, o que concede moita flexibilidade pero tamén máis responsabilidade ao programador. En cambio, linguaxes como Java ou C# optan por un modelo máis estrito no que os obxectos sempre viven no heap, simplificando a xestión da memoria e evitando erros como accesos a memoria liberada.
A recolección de basura (garbage collection) é un mecanismo automático que elimina da memoria os obxectos que xa non están en uso, é dicir, aqueles aos que non queda ningunha referencia activa. Isto evita que o programador teña que liberar manualmente a memoria, como ocorre en C ou C++. Grazas a este sistema, redúcese o risco de fugas de memoria e de referencias colgantes, permitindo centrarse na lóxica do programa máis que na súa xestión de recursos.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

### Respuesta:
Un método é unha función definida dentro dunha clase que describe unha acción ou comportamento que os obxectos desa clase poden realizar. Nun paradigma orientado a obxectos, os métodos actúan sobre o estado interno do obxecto ou realizan operacións relacionadas coa súa funcionalidade. A súa estrutura inclúe un tipo de retorno, un nome, unha lista de parámetros e un corpo que contén as instrucións que executará. En Java, todos os métodos deben formar parte dunha clase, xa que non existen funcións libres como en C.
A sobrecarga de métodos consiste en definir varios métodos co mesmo nome dentro dunha mesma clase, pero diferenciándose polo número ou tipo dos seus parámetros. Este mecanismo permite ofrecer varias versións dunha mesma acción, adaptadas a diferentes necesidades, mantendo un nome coherente que mellora a claridade do código. O compilador selecciona automaticamente a versión adecuada do método en función dos argumentos utilizados ao chamalo, polo que non hai ambigüidade durante a execución.
Este concepto non debe confundirse coa redefinición de métodos, que ocorre cando unha clase filla modifica o comportamento herdado dunha clase pai. A sobrecarga prodúcese dentro da mesma clase e baséase exclusivamente en ter varias firmas distintas para un mesmo nome. Grazas a este recurso, a programación faise máis flexible e expresiva, permitindo ofrecer múltiples formas de executar unha mesma operación sen recorrer a nomes diferentes e innecesariamente complexos.



## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

### Respuesta:
La clase define los atributos como enteros con visibilidad por defecto (es decir, sin public, private ni protected). El método usa la fórmula de la distancia euclídea sqrt(x² + y²), aprovechando Math.sqrt y una conversión a double para obtener un resultado en coma flotante. En el ejemplo de uso, se instancian los valores de x e y asignándolos directamente, se invoca el método y se muestra el resultado por consola. Se incluye un main sencillo para ejecutar la prueba.

// Clase mínima con visibilidad por defecto en los atributos
class Punto {
    int x; // visibilidad por defecto (package-private)
    int y; // visibilidad por defecto (package-private)

    double calculaDistanciaAOrigen() {
        return Math.sqrt((double) (x * x + y * y));
    }
}

// Ejemplo de uso
public class Main {
    public static void main(String[] args) {
        Punto p = new Punto();
        p.x = 3;
        p.y = 4;

        double d = p.calculaDistanciaAOrigen();
        System.out.println("Distancia al origen: " + d); // Debería imprimir 5.0
    }
}



## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

### Respuesta:
O punto de entrada dun programa en Java é sempre o método main coa forma exacta public static void main(String[] args). Cando se executa unha aplicación, a Máquena Virtual de Java busca ese método e comeza a execución a partir del. A presenza da palabra static é fundamental porque permite chamar ao método sen crear previamente un obxecto da clase onde se atopa, algo necesario para iniciar o programa antes de que exista ningunha instancia.
O modificador static indica que un membro (método ou atributo) pertence á clase e non aos obxectos individuais. Isto significa que pode empregarse sen crear instancias e que é compartido por todas elas. Non se utiliza só para o método main; tamén se emprega en variables compartidas, métodos auxiliares ou constantes que non dependen do estado dos obxectos. O uso de static, por tanto, permite definir elementos comúns que existen de maneira global dentro da clase.
A combinación static final adoita utilizarse para declarar constantes, é dicir, valores que pertencen á clase e que non poden modificarse unha vez definidos. O modificador final impide que a variable cambie, garantindo que manteña sempre o mesmo valor durante a execución. A unión de ambos facilita definir elementos como static final double PI = 3.14159;, creando constantes accesibles sen necesidade de instancias e cun valor garantido como inmutable.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

### Respuesta:
Para compilar un programa Java desde a liña de comandos emprégase o compilador javac. Primeiro cómpilase o ficheiro .java e, se non hai erros, xeranse un ou varios ficheiros .class. Estes conteñen o bytecode, que é unha representación intermedia do programa. Unha vez xerados, o programa execútase coa orde java, indicando o nome da clase que contén o método main. Por exemplo:


javac Main.java
java Main

Java considérase un linguaxe compilado e interpretado ao mesmo tempo. Primeiro compílase a bytecode, que non depende do sistema operativo nin da arquitectura. A continuación, ese bytecode interprétase ou se optimiza xusto a tempo (JIT) na plataforma onde se execute. Este modelo híbrido fai que o mesmo programa poida executarse en Windows, Linux, macOS ou outros sistemas sen recompilar.
A Máquina Virtual de Java (JVM) é o sistema encargado de executar o bytecode xerado pola compilación. Actúa como unha capa intermedia entre o programa e o sistema operativo, ofrecendo seguridade, portabilidade e xestión automática da memoria. Grazas á JVM, o mesmo bytecode pode funcionar en calquera dispositivo que dispoña dunha implementación compatible, cumprindo o principio write once, run anywhere.
O bytecode é unha forma de código compacto e independente da plataforma que se almacena nos ficheiros .class. Estes ficheiros conteñen as instrucións que a JVM sabe interpretar. Non é código máquina real, pero tampouco é código fonte; é un formato intermedio optimizado para permitir execución segura e eficiente en diferentes plataformas. Esta separación entre compilación e execución é unha das claves da portabilidade de Java.


## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

### Respuesta:
En Java, new es el operador que reserva memoria en el heap y crea un objeto de una clase, devolviendo una referencia a esa nueva instancia. Al usar new, se invoca automáticamente un constructor, que es un método especial con el mismo nombre que la clase y sin tipo de retorno, cuya función es inicializar el estado del objeto (asignar valores iniciales a sus atributos y, si procede, realizar comprobaciones básicas).
Un constructor puede estar sobrecargado (varias versiones con distintos parámetros) y puede incluir lógica de validación; si no se define ninguno, Java proporciona un constructor por defecto (sin parámetros). En el ejemplo de Punto anterior, new Punto() crea la instancia y llama al constructor por defecto de Punto. A continuación, se muestra un ejemplo de clase Empleado con atributos dni, nombre y apellidos, y un constructor que los inicializa.


public class Empleado {
    // Atributos (visibilidad de ejemplo; puede ajustarse según necesidad)
    private String dni;
    private String nombre;
    private String apellidos;

    // Constructor que inicializa todos los campos
    public Empleado(String dni, String nombre, String apellidos) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellidos = apellidos;
    }

    // Getters de ejemplo (opcionales para el ejercicio)
    public String getDni() { return dni; }
    public String getNombre() { return nombre; }
    public String getApellidos() { return apellidos; }
}


## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

### Respuesta:
En Java, this es una referencia al objeto actual dentro del contexto de una instancia. Se utiliza para desambiguar entre atributos y parámetros con el mismo nombre, para encadenar constructores (this(...)) y para pasar la referencia del propio objeto a otros métodos. Su finalidad es dejar claro que se está accediendo a los campos o métodos de instancia del objeto sobre el que se está trabajando en ese momento.
No todos los lenguajes lo llaman igual, aunque el concepto es muy similar. Por ejemplo, en C++ y JavaScript se emplea también this, mientras que en Python se usa el parámetro explícito self en los métodos de instancia. La idea general es la misma: disponer de una referencia al objeto receptor del método para acceder a su estado y comportamiento.

// Clase Punto con uso ilustrativo de 'this'
class Punto {
    int x;  // visibilidad por defecto
    int y;  // visibilidad por defecto

    // Constructor: desambiguación entre parámetros y atributos
    Punto(int x, int y) {
        this.x = x;   // 'this.x' = atributo; 'x' = parámetro
        this.y = y;
    }

    // Encadenamiento de constructores usando this(...)
    Punto() {
        this(0, 0);   // llama al otro constructor con (0,0)
    }

    // Método de instancia que usa this para invocar otro método
    double calculaDistanciaAOrigen() {
        return this.distanciaA(0, 0);
    }

    // Método auxiliar
    double distanciaA(int x2, int y2) {
        int dx = this.x - x2;
        int dy = this.y - y2;
        return Math.sqrt((double)(dx * dx + dy * dy));
    }
}


## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

### Respuesta:
Para calcular la distancia entre el objeto actual (this) y otro punto, se define un método distanciaA(Punto otro) que reciba un parámetro de tipo Punto. La implementación aplica la fórmula de la distancia euclídea entre dos puntos en el plano: sqrt((x1 - x2)^2 + (y1 - y2)^2). Se mantiene la visibilidad por defecto en los atributos x e y para ser coherente con los ejercicios previos; el método accede a this.x y this.y para referirse a las coordenadas del objeto receptor.
También puede añadirse un método auxiliar que calcule la distancia al origen o una sobrecarga que reciba coordenadas int, pero para el requisito actual basta con aceptar un Punto como argumento. En el ejemplo de uso, se crean dos instancias y se invoca p1.distanciaA(p2), imprimiendo el resultado en consola. El código completo es ejecutable en un único archivo con una clase Main que contiene el método main.

// Clase Punto con visibilidad por defecto en los atributos
class Punto {
    int x;  // visibilidad por defecto (package-private)
    int y;  // visibilidad por defecto (package-private)

    // Constructores opcionales para facilitar pruebas
    Punto() { this(0, 0); }
    Punto(int x, int y) {
        this.x = x;
        this.y = y;
    }

    // Distancia al origen (opcional)
    double calculaDistanciaAOrigen() {
        return Math.sqrt((double) (x * x + y * y));
    }

    // >>> Método solicitado: distancia entre 'this' y otro punto
    double distanciaA(Punto otro) {
        int dx = this.x - otro.x;
        int dy = this.y - otro.y;
        return Math.sqrt((double) (dx * dx + dy * dy));
    }
}

// Ejemplo ejecutable
public class Main {
    public static void main(String[] args) {
        Punto p1 = new Punto(3, 4);
        Punto p2 = new Punto(0, 0);

        double d = p1.distanciaA(p2); // debería ser 5.0
        System.out.println("Distancia entre p1 y p2: " + d);
    }
}


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

### Respuesta:
En Java, todo se pasa por valor. Cuando se pasa un objeto (como Punto) a un método, lo que se copia es el valor de la referencia. Por ello, si dentro del método se modifican atributos del objeto referenciado (por ejemplo, p.x = 10;), esos cambios sí afectan al objeto fuera del método, porque tanto el parámetro como la variable del llamador apuntan al mismo objeto en el heap. Sin embargo, si dentro del método se reasigna el parámetro (p = new Punto()), esa nueva referencia no se propaga al exterior, ya que solo cambia la copia local de la referencia.
En cambio, para tipos primitivos como int, también se pasa por valor, pero aquí el valor es el contenido numérico. Si se recibe un int y se le cambia el valor dentro del método (por ejemplo, n = 99;), no afecta a la variable original del llamador, porque lo que se modificó fue únicamente la copia local del entero. Este comportamiento diferencia claramente “modificar el estado del objeto apuntado” (que sí impacta fuera) de “cambiar qué referencia o valor primitivo tiene el parámetro” (que no impacta fuera).

// Ejemplo con objeto: modificar atributos SÍ afecta fuera
void mueveXPunto(Punto p) { p.x += 10; }    // cambia el estado del mismo objeto
void reasignaPunto(Punto p) { p = new Punto(0,0); } // NO cambia la referencia externa

// Ejemplo con primitivo: NO afecta fuera
void incrementa(int n) { n++; } // 'n' es una copia, el original no cambia


## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

### Respuesta:
En Java, toString() es un método heredado de Object que devuelve una representación textual del objeto. Al sobrescribirlo en una clase, se puede controlar cómo se mostrará el objeto al imprimirlo (por ejemplo, con System.out.println(obj)) o al concatenarlo con cadenas. Su objetivo es ofrecer una descripción legible y útil del estado interno relevante, en lugar de la representación por defecto que incluye el nombre de la clase y un identificador de hash.
Este concepto existe en otros lenguajes con nombres o mecanismos similares. En C#, se usa también ToString() para obtener la representación textual de un objeto. En Python, la función equivalente es __str__ (y para representación técnica __repr__). En C++, no hay un método estándar llamado así, pero se suele lograr un efecto equivalente sobrecargando el operador de inserción << para std::ostream.
A continuación, se muestra un ejemplo de toString() en la clase Punto. La implementación devuelve las coordenadas en formato legible, y su uso permite imprimir la instancia directamente.

class Punto {
    int x; // visibilidad por defecto
    int y; // visibilidad por defecto

    Punto() { this(0, 0); }
    Punto(int x, int y) {
        this.x = x;
        this.y = y;
    }

    double calculaDistanciaAOrigen() {
        return Math.sqrt((double) (x * x + y * y));
    }

    double distanciaA(Punto otro) {
        int dx = this.x - otro.x;
        int dy = this.y - otro.y;
        return Math.sqrt((double) (dx * dx + dy * dy));
    }

    @Override
    public String toString() {
        return "Punto(" + x + ", " + y + ")";
    }
}

// Ejemplo de uso
public class Main {
    public static void main(String[] args) {
        Punto p = new Punto(3, 4);
        System.out.println(p); // imprime: Punto(3, 4)
    }
}


## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


### Respuesta:
Un struct de C pode lembrarse superficialmente a unha clase porque ambos permiten agrupar datos baixo un mesmo tipo. Con todo, o struct é só unha colección de variables, sen comportamento asociado. Non pode ter métodos, non pode ter construtores, nin permite controlar a visibilidade dos seus campos. É simplemente un contenedor estático de datos, útil para organizar información pero incapaz de expresar comportamento nin garantir como se manipulan eses datos.
Para que un struct fose equivalente a unha clase, debería ter a capacidade de combinar datos e funcións nunha mesma unidade lógica. Nunha clase, as variables de instancia forman o estado do obxecto, e os métodos definen o seu comportamento, algo imposible de reproducir en C sen recorrer a punteiros a funcións ou patróns máis complexos. Tamén lle falta a posibilidade de ter construtores, que inicialicen automaticamente o estado ao crear unha instancia, e modificadores de acceso como private, fundamentais para o encapsulamento en orientación a obxectos.
Finalmente, nunha clase os obxectos creados son instancias reais, con comportamento propio, identidade e ciclo de vida xestionado por mecanismos como o heap e a recolección de lixo. Un struct en C carece por completo deses conceptos: non ten métodos implícitos, non existe herdanza, non hai polimorfismo nin ningunha das características típicas da POO. Por tanto, un struct pode considerarse un paso inicial para entender a organización de datos, pero está moi lonxe de ser unha clase tal e como se entende na programación orientada a obxectos.


## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

### Respuesta:
En C puede emularse una clase definiendo un struct para el estado y funciones externas para el comportamiento. No existen métodos dentro del struct, pero se puede seguir una convención de nombres (por ejemplo, Punto_calculaDistanciaAOrigen) y pasar un puntero al struct como primer parámetro de cada función. Ese puntero hace el papel de this: señala explícitamente al objeto (instancia) sobre el que se opera. No hay constructores ni modificadores de acceso; la inicialización se realiza manualmente o con funciones auxiliares que devuelven un Punto ya configurado.
Al no existir encapsulación nativa, los campos x e y quedan públicos por defecto y modificables desde cualquier lugar. Esto simplifica el ejemplo pero renuncia a garantías de integridad que sí ofrece una clase en Java con private y métodos de acceso. A cambio, se obtiene un patrón claro: datos en el struct y operaciones como funciones que reciben un puntero a esos datos. Este estilo aproxima la organización OO usando herramientas del C estándar.
A continuación se muestra una emulación mínima de la clase Punto con una función que calcula la distancia al origen. Obsérvese cómo el parámetro self (puntero a Punto) sustituye al this implícito de Java.

/* Emulación de clase Punto en C */

#include <stdio.h>
#include <math.h>

typedef struct {
    int x;
    int y;
} Punto;

/* “Constructor” opcional (función de ayuda) */
Punto Punto_crear(int x, int y) {
    Punto p;
    p.x = x;
    p.y = y;
    return p;
}

/* Método “de instancia”: recibe un puntero que hace de `this` */
double Punto_calculaDistanciaAOrigen(const Punto *self) {
    /* `self` es el “this” explícito */
    return sqrt((double)(self->x * self->x + self->y * self->y));
}

int main(void) {
    /* Inicialización manual o usando la función “constructor” */
    Punto p = Punto_crear(3, 4);
    /* Alternativa: Punto p = { .x = 3, .y = 4 }; */

    double d = Punto_calculaDistanciaAOrigen(&p);
    printf("Distancia al origen: %.1f\n", d); /* Imprime 5.0 */

    return 0;
}

En resumen, en C no existe this implícito; su papel lo cumple el puntero que se pasa a las funciones que actúan como métodos. Con este patrón se reproduce la separación estado + comportamiento propia de la POO, aunque sin características como encapsulación, constructores, herencia o polimorfismo.
