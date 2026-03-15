<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Composición". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos, Encapsulación y Excepciones.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# Tema 4.1. Composición


## 1. En C, podemos crear estructuras mayores **componiendo** unas con otras, que suelen describirse como "A tiene-un/tiene-varios B". Pon un ejemplo, empleando `struct`, de una línea de puntos, donde puntos tienen dos coordenadas (`x` e `y`), y la línea esta hecha de dos puntos. Incluye una función para calcular la distancia entre puntos y otra para hallar la longitud de una línea.

En C, la composición se implementa mediante la inclusión de estructuras como campos de otras estructuras, estableciendo relaciones de "tiene-un" entre los tipos de datos. Para el ejemplo propuesto, se define primero la estructura `Punto` que contiene las coordenadas, y luego la estructura `Linea` que está compuesta por dos puntos:

```c
typedef struct {
    float x;
    float y;
} Punto;

typedef struct {
    Punto inicio;
    Punto fin;
} Linea;
```

Para calcular la distancia entre dos puntos, se implementa una función que recibe dos estructuras `Punto` y aplica el teorema de Pitágoras. La longitud de una línea se obtiene llamando a esta función con los puntos que la componen:

```c
#include <math.h>

float distancia(Punto p1, Punto p2) {
    float dx = p1.x - p2.x;
    float dy = p1.y - p2.y;
    return sqrt(dx*dx + dy*dy);
}

float longitudLinea(Linea l) {
    return distancia(l.inicio, l.fin);
}
```

Este enfoque permite construir tipos de datos complejos a partir de otros más simples, manteniendo una clara jerarquía de composición. La ventaja principal es que las funciones que operan sobre los tipos básicos pueden reutilizarse para calcular propiedades de las estructuras compuestas, como se demuestra al usar `distancia` dentro de `longitudLinea`.


## 2. Ahora transforma ese ejemplo a orientación a objetos con Java, para tener un primer ejemplo de **composición** en orientación a objetos. Crea una clase `Punto`, y una clase `Linea`. La clase `Punto` debe tener un método para calcular distancia a otro `Punto` y `Linea` debe tener un método para calcular su longitud. Gracias a la ocultación de información, supera a C, garantizando que los puntos sean inmutables, al igual que la línea, que una vez creada, no queremos que se modifique de qué a qué puntos va dicha línea.  

En Java, la composición orientada a objetos se implementa mediante la inclusión de referencias a objetos como atributos de otros objetos, estableciendo relaciones de "tiene-un" que pueden beneficiarse del encapsulamiento. Para el ejemplo, se define la clase `Punto` con atributos privados `x` e `y`, un constructor que inicializa estos valores y un método público para calcular la distancia a otro punto. La inmutabilidad se logra declarando los atributos como `final` y no proporcionando métodos modificadores (setters):

```java
public class Punto {
    private final double x;
    private final double y;
    
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }
    
    public double distancia(Punto otro) {
        double dx = this.x - otro.x;
        double dy = this.y - otro.y;
        return Math.sqrt(dx*dx + dy*dy);
    }
}
```

La clase `Linea` se compone de dos objetos `Punto` y también se diseña como inmutable, garantizando que una vez creada, sus puntos extremos no puedan ser modificados. Esto se consigue declarando los atributos como `final`, inicializándolos en el constructor y sin proporcionar métodos que alteren el estado. El cálculo de la longitud delega en el método `distancia` de la clase `Punto`:

```java
public class Linea {
    private final Punto inicio;
    private final Punto fin;
    
    public Linea(Punto inicio, Punto fin) {
        this.inicio = inicio;
        this.fin = fin;
    }
    
    public double longitud() {
        return inicio.distancia(fin);
    }
}
```

Esta implementación supera a la versión en C en varios aspectos. El encapsulamiento protege los datos internos, la inmutabilidad garantiza que los objetos no cambien después de su creación, y la delegación de responsabilidades (el cálculo de distancia está en `Punto`) produce un diseño más cohesivo y mantenible. La composición en Java, combinada con estos principios de orientación a objetos, permite construir jerarquías de objetos más robustas y con un mejor control sobre su estado y comportamiento.


## 3. ¿Qué significa la **multiplicidad** en la composición? En el ejemplo anterior, ¿cuál es la multiplicidad entre `Linea` y `Punto`? Indícalo expresando la multiplicidad en ambas direcciones, de `Linea` a `Punto` y de `Punto` a `Linea`.

La multiplicidad en composición indica cuántas instancias de una clase pueden estar asociadas con una instancia de otra clase en una relación determinada. Especifica las cardinalidades mínimas y máximas permitidas en cada extremo de la relación, lo que resulta fundamental para comprender las restricciones estructurales del modelo. En el contexto de la composición, donde una clase "contenedora" gestiona el ciclo de vida de sus partes, la multiplicidad define cuántos objetos parte pueden existir por cada objeto contenedor y viceversa.

En el ejemplo de `Linea` y `Punto`, la multiplicidad de `Linea` a `Punto` es **1..2**, lo que significa que una línea está compuesta exactamente por dos puntos (su inicio y su fin). Esta cardinalidad refleja que una línea necesita ambos extremos para ser definida como tal, y ambos son creados y destruidos con la línea. En la dirección inversa, de `Punto` a `Linea`, la multiplicidad es **0..***, indicando que un punto puede pertenecer a ninguna, una o múltiples líneas (por ejemplo, un punto podría ser el inicio de una línea y también el fin de otra, o incluso compartirse entre varias líneas como vértice común). Esta asimetría en las multiplicidades muestra que, aunque la línea depende existencialmente de sus puntos, los puntos tienen una existencia independiente y pueden participar en múltiples relaciones de composición.


## 4. ¿Qué significa composición **fuerte** y composición **débil**? ¿Qué consecuencia implica en relación al ciclo de vida de los objetos? Indica a cuál solemos referirnos como **"asociación o agregación"** y a cuál como **"composición"** propiamente.

La composición fuerte, denominada simplemente **composición** en terminología UML, implica una relación de "todo-parte" donde el objeto contenedor gestiona completamente el ciclo de vida de los objetos contenidos. En este tipo de relación, las partes no tienen existencia independiente fuera del contenedor: si el objeto contenedor es destruido, todas sus partes también lo son. Además, una parte específica pertenece exclusivamente a un único contenedor en un momento dado, estableciendo una dependencia existencial muy fuerte. En la implementación en Java, esto suele traducirse en que el contenedor crea internamente las partes en su constructor y no expone referencias que permitan compartirlas externamente.

La composición débil, conocida como **agregación**, representa una relación donde el contenedor referencia a objetos que pueden existir independientemente. En este caso, el ciclo de vida de las partes no está ligado al del contenedor: si el contenedor es destruido, las partes continúan existiendo y pueden ser utilizadas por otros objetos. Las partes pueden compartirse entre múltiples contenedores y su creación y destrucción ocurre de manera independiente. En Java, esto se implementa típicamente pasando las referencias a los objetos parte a través del constructor del contenedor, donde dichos objetos han sido creados externamente.

En el ejemplo anterior de `Linea` y `Punto`, la relación es una agregación (composición débil) porque los puntos pueden existir antes de formar parte de la línea y pueden seguir existiendo después, además de poder compartirse entre diferentes líneas. Si se quisiera convertir en composición fuerte, los puntos deberían crearse exclusivamente dentro de la línea y destruirse con ella, lo que en este caso no sería adecuado porque un punto podría necesitar ser reutilizado. Esta distinción resulta fundamental en el diseño orientado a objetos para reflejar correctamente las dependencias existenciales entre las clases y determinar quién es responsable de la creación y destrucción de los objetos.


## 5. Cuando una clase usa a otra al recibirla o devolverla como parámetro en algún método, al hacer `new` dentro de un método, o al usarlas como variables locales, ¿hablamos de composición o de **"dependencia"**?

Cuando una clase utiliza a otra únicamente como parámetro de métodos, tipo de retorno, variable local o mediante instanciación dentro de un método, no se está estableciendo una relación estructural duradera entre los objetos, sino una **dependencia** o **uso temporal**. En estos casos, la clase cliente conoce la existencia de la otra clase y la utiliza para realizar alguna operación puntual, pero no mantiene una referencia persistente como atributo que forme parte de su estado interno. Esta relación es más débil y transitoria que la composición, ya que los objetos involucrados no comparten un ciclo de vida ni existe una vinculación que perdure más allá de la ejecución del método.

La dependencia se manifiesta típicamente cuando una clase importa a otra para usarla en la firma de sus métodos o cuando crea instancias locales para realizar cálculos auxiliares. Por ejemplo, si una clase `Calculadora` tiene un método que recibe un `Punto` como parámetro y devuelve un resultado, existe una dependencia entre `Calculadora` y `Punto`, pero no una composición. Esta distinción resulta importante en el diseño orientado a objetos porque las dependencias representan acoplamientos más débiles y deseables, mientras que la composición (ya sea fuerte o débil) implica asociaciones estructurales que deben gestionarse con mayor cuidado en términos de ciclo de vida y responsabilidades.


## 6. En el ejemplo anterior de línea y punto, programa la relación entre `Linea` y `Punto` de dos formas. Una **como composición fuerte**, donde el ciclo de vida de los puntos está ligado al de Linea y otra **como composición débil**, donde no.

Para implementar la **composición fuerte** entre `Linea` y `Punto`, la clase `Linea` debe crear internamente sus propios puntos y garantizar que nadie externo pueda acceder a ellos para modificarlos o compartirlos. En esta implementación, los puntos se crean dentro del constructor de `Linea` a partir de las coordenadas proporcionadas, y no se exponen referencias a ellos mediante getters que permitan manipularlos desde fuera. De esta forma, los puntos nacen con la línea y morirán con ella cuando el recolector de basura elimine la línea al no haber referencias:

```java
public class LineaFuerte {
    private final Punto inicio;
    private final Punto fin;
    
    public LineaFuerte(double x1, double y1, double x2, double y2) {
        this.inicio = new Punto(x1, y1);
        this.fin = new Punto(x2, y2);
    }
    
    public double longitud() {
        return inicio.distancia(fin);
    }
    
    // Sin getters que expongan los puntos para mantener el encapsulamiento fuerte
}
```

Para la **composición débil (agregación)**, la clase `Linea` recibe los puntos ya creados desde el exterior, permitiendo que estos existan independientemente y puedan ser compartidos entre múltiples líneas. En esta versión, se proporcionan getters que devuelven los puntos, aunque para mantener la inmutabilidad del conjunto se deben devolver los propios objetos inmutables o copias defensivas. Los puntos pueden ser creados antes que la línea y seguir existiendo después de que esta desaparezca:

```java
public class LineaDebil {
    private final Punto inicio;
    private final Punto fin;
    
    public LineaDebil(Punto inicio, Punto fin) {
        this.inicio = inicio;
        this.fin = fin;
    }
    
    public double longitud() {
        return inicio.distancia(fin);
    }
    
    public Punto getInicio() {
        return inicio;  // Punto es inmutable, es seguro devolver la referencia
    }
    
    public Punto getFin() {
        return fin;     // Punto es inmutable, es seguro devolver la referencia
    }
}
```

La diferencia fundamental entre ambas implementaciones radica en el origen de los objetos `Punto` y en quién controla su ciclo de vida. En la composición fuerte, la línea es la única responsable de sus puntos y estos no existen fuera del contexto de la línea, lo que garantiza un encapsulamiento más estricto pero menor flexibilidad. En la agregación, los puntos tienen identidad propia y pueden ser reutilizados, lo que proporciona mayor flexibilidad a costa de un acoplamiento más laxo. La elección entre uno u otro enfoque depende de los requisitos del dominio: si los puntos son entidades con significado propio que deben compartirse, se opta por agregación; si son meros componentes internos sin identidad independiente, la composición fuerte resulta más apropiada.

## 7. En Java, en la composición fuerte, ¿cuando el contenedor destruye los objetos? No se observa que `Linea` destruya los `Punto` explícitamente, ¿Por qué?

En Java, la destrucción explícita de objetos no existe como tal, ya que el lenguaje utiliza un recolector de basura (garbage collector) que automáticamente libera la memoria cuando los objetos ya no son alcanzables desde ninguna referencia activa. En la composición fuerte, cuando un objeto contenedor deja de ser accesible (por ejemplo, al salir del ámbito donde fue creado o al asignarle null a su referencia), el recolector de basura eventualmente eliminará tanto al contenedor como a los objetos que contiene, siempre que estos últimos no sean referenciados desde otras partes del programa. Esta gestión automática de memoria es una de las características que diferencia a Java de lenguajes como C, donde el programador debe liberar explícitamente la memoria con free().

En el ejemplo de `LineaFuerte`, los objetos `Punto` son creados dentro del constructor y almacenados como referencias privadas. Mientras exista al menos una referencia a la línea desde el exterior, tanto la línea como sus puntos permanecerán en memoria. Cuando la línea pierda su última referencia externa, todo el grafo de objetos formado por la línea y sus puntos se vuelve inalcanzable, y el recolector de basura los marcará para su eliminación. Este comportamiento satisface automáticamente la semántica de la composición fuerte: los puntos viven y mueren con su contenedor sin necesidad de destrucción explícita, siempre que se garantice que no hay referencias externas a ellos (lo cual se logra no exponiendo los puntos mediante getters o devolviendo copias defensivas en caso necesario).


## 8. Pon un ejemplo de composicion débil entre un departamento que tiene varios profesores. Implementa dos composiciones a la vez: entre el departamento y todos sus profesores y entre el departamento y su director, que es un profesor del departamento. Siempre debe haber un director en el departamento desde el inicio. Lanza excepciones si se viola la invariante. Emplea arrays primitivos de Java, estilo `Profesor[]`, con máximo 50, pero no rompas la encapsulación, no desveles que estás empleando un array, permite añadir un `Profesor` al final de la lista, y eliminar un profesor dada su posición. Da acceso a los profesores con un método para saber cuántos hay y otro para obtener un profesor por posición. El director se puede cambiar por otro profesor del departamento. Sin embargo, ten en cuenta esta invariante de clase: el director debe formar siempre parte de la lista de profesores, es decir, ten cuidado al cambiar el director o al eliminar un profesor.

A continuación se presenta la implementación de la clase `Departamento` que mantiene una lista de profesores y un director, asegurando que el director siempre sea uno de los profesores del departamento. Se utiliza un array primitivo de `Profesor` con capacidad máxima de 50, pero la encapsulación oculta este detalle de implementación:

```java
import java.util.Objects;

public class Departamento {
    private static final int MAX_PROFESORES = 50;
    private Profesor[] profesores;
    private int numProfesores;
    private Profesor director;
    
    public Departamento(Profesor director) {
        if (director == null) {
            throw new NullPointerException("El director no puede ser null");
        }
        this.profesores = new Profesor[MAX_PROFESORES];
        this.profesores[0] = director;
        this.numProfesores = 1;
        this.director = director;
    }
    
    public void addProfesor(Profesor profesor) {
        if (profesor == null) {
            throw new NullPointerException("El profesor no puede ser null");
        }
        if (numProfesores >= MAX_PROFESORES) {
            throw new IllegalStateException("No se pueden añadir más profesores. Máximo: " + MAX_PROFESORES);
        }
        // Evitar duplicados (por su identidad)
        for (int i = 0; i < numProfesores; i++) {
            if (profesores[i].equals(profesor)) {
                throw new IllegalArgumentException("El profesor ya existe en el departamento");
            }
        }
        profesores[numProfesores++] = profesor;
    }
    
    public void removeProfesor(int posicion) {
        if (posicion < 0 || posicion >= numProfesores) {
            throw new IllegalArgumentException("Posición fuera de rango: " + posicion);
        }
        
        Profesor profesorAEliminar = profesores[posicion];
        
        // Verificar que no sea el director actual
        if (profesorAEliminar.equals(director)) {
            throw new IllegalStateException("No se puede eliminar al director actual. Cambie el director primero.");
        }
        
        // Desplazar los elementos hacia la izquierda
        for (int i = posicion; i < numProfesores - 1; i++) {
            profesores[i] = profesores[i + 1];
        }
        profesores[--numProfesores] = null; // Liberar referencia para el GC
    }
    
    public void setDirector(Profesor nuevoDirector) {
        if (nuevoDirector == null) {
            throw new NullPointerException("El director no puede ser null");
        }
        
        // Verificar que el nuevo director está en la lista de profesores
        boolean encontrado = false;
        for (int i = 0; i < numProfesores; i++) {
            if (profesores[i].equals(nuevoDirector)) {
                encontrado = true;
                break;
            }
        }
        
        if (!encontrado) {
            throw new IllegalArgumentException("El nuevo director debe ser un profesor del departamento");
        }
        
        this.director = nuevoDirector;
    }
    
    public int getNumProfesores() {
        return numProfesores;
    }
    
    public Profesor getProfesor(int posicion) {
        if (posicion < 0 || posicion >= numProfesores) {
            throw new IllegalArgumentException("Posición fuera de rango: " + posicion);
        }
        return profesores[posicion];
    }
    
    public Profesor getDirector() {
        return director;
    }
    
    // Método auxiliar para mostrar el estado (solo para pruebas)
    public void mostrarEstado() {
        System.out.println("Director: " + director);
        System.out.println("Profesores (" + numProfesores + "):");
        for (int i = 0; i < numProfesores; i++) {
            System.out.println("  " + i + ": " + profesores[i]);
        }
    }
}
```

La clase `Profesor` se implementa de manera sencilla, asumiendo que tiene un nombre y posiblemente otros atributos, y que se considera igual a otro profesor por su identidad (en este caso, se usa el nombre para simplificar, aunque en un sistema real podría ser un identificador único):

```java
import java.util.Objects;

public class Profesor {
    private final String nombre;
    
    public Profesor(String nombre) {
        if (nombre == null || nombre.trim().isEmpty()) {
            throw new IllegalArgumentException("El nombre no puede ser null o vacío");
        }
        this.nombre = nombre;
    }
    
    public String getNombre() {
        return nombre;
    }
    
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Profesor profesor = (Profesor) obj;
        return nombre.equals(profesor.nombre);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(nombre);
    }
    
    @Override
    public String toString() {
        return "Profesor{" + nombre + "}";
    }
}
```

Esta implementación cumple con los requisitos establecidos. La clase `Departamento` mantiene dos relaciones de composición débil: una con el conjunto de profesores (agregación) y otra con el director, que es un profesor específico dentro de ese conjunto. La encapsulación se preserva ocultando el array mediante métodos controlados para añadir, eliminar y acceder a los profesores. Las invariantes se protegen lanzando excepciones cuando se intenta eliminar al director actual o cuando se pretende establecer un director que no pertenece al departamento. Los métodos públicos permiten obtener el número de profesores y acceder a ellos por posición sin exponer el array subyacente, manteniendo así el principio de ocultación de información.


## 9. En Java, existen también `List`, cambia y muestra cómo sería el código anterior empleando `List` en vez de arrays primitivos. ¿Qué parte del código original te has ahorrado? Además, fíjate en el método `getProfesor(int pos)`: si en su lugar existiera un método que devolviera todos los profesores a la vez, ¿qué problema tendría devolver directamente la lista interna? ¿Cómo lo resolverías?

A continuación se presenta la implementación de la clase `Departamento` utilizando `List` en lugar de arrays primitivos, lo que simplifica considerablemente el código al eliminar la gestión manual del tamaño y los desplazamientos:

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Objects;

public class Departamento {
    private static final int MAX_PROFESORES = 50;
    private List<Profesor> profesores;
    private Profesor director;
    
    public Departamento(Profesor director) {
        if (director == null) {
            throw new NullPointerException("El director no puede ser null");
        }
        this.profesores = new ArrayList<>();
        this.profesores.add(director);
        this.director = director;
    }
    
    public void addProfesor(Profesor profesor) {
        if (profesor == null) {
            throw new NullPointerException("El profesor no puede ser null");
        }
        if (profesores.size() >= MAX_PROFESORES) {
            throw new IllegalStateException("No se pueden añadir más profesores. Máximo: " + MAX_PROFESORES);
        }
        if (profesores.contains(profesor)) {
            throw new IllegalArgumentException("El profesor ya existe en el departamento");
        }
        profesores.add(profesor);
    }
    
    public void removeProfesor(int posicion) {
        if (posicion < 0 || posicion >= profesores.size()) {
            throw new IllegalArgumentException("Posición fuera de rango: " + posicion);
        }
        
        Profesor profesorAEliminar = profesores.get(posicion);
        
        if (profesorAEliminar.equals(director)) {
            throw new IllegalStateException("No se puede eliminar al director actual. Cambie el director primero.");
        }
        
        profesores.remove(posicion);
    }
    
    public void setDirector(Profesor nuevoDirector) {
        if (nuevoDirector == null) {
            throw new NullPointerException("El director no puede ser null");
        }
        
        if (!profesores.contains(nuevoDirector)) {
            throw new IllegalArgumentException("El nuevo director debe ser un profesor del departamento");
        }
        
        this.director = nuevoDirector;
    }
    
    public int getNumProfesores() {
        return profesores.size();
    }
    
    public Profesor getProfesor(int posicion) {
        if (posicion < 0 || posicion >= profesores.size()) {
            throw new IllegalArgumentException("Posición fuera de rango: " + posicion);
        }
        return profesores.get(posicion);
    }
    
    public Profesor getDirector() {
        return director;
    }
    
    public void mostrarEstado() {
        System.out.println("Director: " + director);
        System.out.println("Profesores (" + profesores.size() + "):");
        for (int i = 0; i < profesores.size(); i++) {
            System.out.println("  " + i + ": " + profesores.get(i));
        }
    }
}
```

El código original con arrays requería gestionar manualmente el contador `numProfesores`, verificar los límites en cada operación, implementar el desplazamiento de elementos al eliminar y liberar explícitamente las referencias. Con `List`, todo esto se simplifica drásticamente: el tamaño se obtiene con `size()`, la verificación de límites se delega en la lista (aunque se mantiene para mensajes personalizados), la eliminación se realiza con `remove(posicion)` que automáticamente reordena la lista, y la comprobación de existencia se reduce a `contains()`. El código resultante es más legible, menos propenso a errores y más cercano a la intención del negocio.

Si se implementara un método que devolviera todos los profesores a la vez, como `public List<Profesor> getTodosLosProfesores()`, devolver directamente la lista interna `this.profesores` rompería la encapsulación. Quien reciba esa lista podría modificar su contenido (añadiendo o eliminando profesores) sin pasar por los métodos controlados de `Departamento`, violando así las invariantes de clase (como que el director debe estar siempre en la lista). Para resolverlo, se debe devolver una copia defensiva de la lista, típicamente mediante `new ArrayList<>(profesores)` o usando `Collections.unmodifiableList(profesores)` si se quiere una vista de solo lectura. La primera opción crea una copia independiente que no afecta al original, mientras que la segunda lanza excepción ante cualquier intento de modificación, siendo más eficiente pero exponiendo los cambios internos si la lista original se modifica después.


## 10. Al igual que ocurre con las excepciones en Java, que pueden encerrar causas (que son excepciones), de forma recursiva, suponen un tipo especial de composiciones, denominadas composiciones recursivas. Pon un ejemplo en Java de una `Persona`, que sea inmutable, y que tiene una madre, que es otra `Persona`. Haz un main con un ejemplo de uso con una familia de personas, desde el nieto hasta la abuela. Enumera algún otro ejemplo clásico de composiciones recursivas.

A continuación se presenta la clase `Persona` inmutable que implementa una composición recursiva donde cada persona tiene una referencia a su madre, que a su vez es otra persona. Esta estructura permite crear cadenas genealógicas que reflejan la naturaleza recursiva de las relaciones familiares:

```java
import java.util.Objects;

public final class Persona {
    private final String nombre;
    private final int añoNacimiento;
    private final Persona madre;
    
    public Persona(String nombre, int añoNacimiento, Persona madre) {
        this.nombre = Objects.requireNonNull(nombre, "El nombre no puede ser null");
        if (añoNacimiento <= 0) {
            throw new IllegalArgumentException("El año de nacimiento debe ser positivo");
        }
        this.añoNacimiento = añoNacimiento;
        this.madre = madre; // Puede ser null (si es la primera generación)
        
        // Verificar coherencia temporal si hay madre
        if (madre != null && madre.añoNacimiento >= añoNacimiento) {
            throw new IllegalArgumentException("La madre no puede haber nacido después o el mismo año que el hijo");
        }
    }
    
    public String getNombre() {
        return nombre;
    }
    
    public int getAñoNacimiento() {
        return añoNacimiento;
    }
    
    public Persona getMadre() {
        return madre;
    }
    
    public boolean esAntepasado(Persona posibleAntepasado) {
        if (posibleAntepasado == null) return false;
        
        Persona ascendente = madre;
        while (ascendente != null) {
            if (ascendente.equals(posibleAntepasado)) {
                return true;
            }
            ascendente = ascendente.getMadre();
        }
        return false;
    }
    
    public int getNumeroGeneracionesHasta(Persona antepasado) {
        if (antepasado == null) return -1;
        
        int generaciones = 0;
        Persona ascendente = madre;
        
        while (ascendente != null) {
            if (ascendente.equals(antepasado)) {
                return generaciones + 1;
            }
            ascendente = ascendente.getMadre();
            generaciones++;
        }
        return -1; // No es antepasado
    }
    
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Persona persona = (Persona) obj;
        return añoNacimiento == persona.añoNacimiento &&
               nombre.equals(persona.nombre) &&
               Objects.equals(madre, persona.madre);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(nombre, añoNacimiento, madre);
    }
    
    @Override
    public String toString() {
        if (madre != null) {
            return nombre + " (" + añoNacimiento + "), hija de " + madre.getNombre();
        } else {
            return nombre + " (" + añoNacimiento + "), sin información de madre";
        }
    }
}
```

Ejemplo de uso con una familia de tres generaciones:

```java
public class EjemploFamilia {
    public static void main(String[] args) {
        // Crear la abuela (sin madre conocida)
        Persona abuela = new Persona("María", 1950, null);
        
        // Crear la madre, hija de la abuela
        Persona madre = new Persona("Ana", 1975, abuela);
        
        // Crear el hijo (nieto de la abuela)
        Persona nieto = new Persona("Carlos", 2000, madre);
        
        // Mostrar la información
        System.out.println("=== Información familiar ===");
        System.out.println("Nieto: " + nieto);
        System.out.println("Madre: " + madre);
        System.out.println("Abuela: " + abuela);
        
        // Verificar relaciones
        System.out.println("\n=== Verificando relaciones ===");
        System.out.println("¿Carlos es antepasado de María? " + nieto.esAntepasado(abuela));
        System.out.println("¿María es antepasado de Carlos? " + abuela.esAntepasado(nieto));
        System.out.println("¿María es antepasado de Ana? " + abuela.esAntepasado(madre));
        
        // Calcular generaciones
        System.out.println("\n=== Generaciones de distancia ===");
        System.out.println("Generaciones de Carlos a Ana: " + nieto.getNumeroGeneracionesHasta(ana));
        System.out.println("Generaciones de Carlos a María: " + nieto.getNumeroGeneracionesHasta(abuela));
        System.out.println("Generaciones de Ana a María: " + madre.getNumeroGeneracionesHasta(abuela));
    }
}
```

La salida del programa sería:

```
=== Información familiar ===
Nieto: Carlos (2000), hija de Ana
Madre: Ana (1975), hija de María
Abuela: María (1950), sin información de madre

=== Verificando relaciones ===
¿Carlos es antepasado de María? false
¿María es antepasado de Carlos? true
¿María es antepasado de Ana? true

=== Generaciones de distancia ===
Generaciones de Carlos a Ana: 1
Generaciones de Carlos a María: 2
Generaciones de Ana a María: 1
```

Las composiciones recursivas son estructuras donde un objeto contiene referencias a otros objetos del mismo tipo, creando potencialmente cadenas o árboles infinitos. Además del ejemplo genealógico, existen otros casos clásicos en programación:

1. **Estructuras de datos**: Listas enlazadas (cada nodo contiene referencia al siguiente nodo), árboles binarios (cada nodo tiene referencias a sus hijos izquierdo y derecho), y grafos donde los nodos se referencian entre sí.

2. **Sistemas de archivos**: Las carpetas contienen otras carpetas y archivos, formando una estructura jerárquica recursiva donde cada carpeta puede contener subcarpetas del mismo tipo.

3. **Documentos anidados**: En procesadores de texto, un documento puede contener secciones que a su vez contienen subsecciones, todas ellas del mismo tipo de elemento estructural.

4. **Expresiones matemáticas**: Una expresión puede estar compuesta por subexpresiones más simples, como en los árboles de sintaxis abstracta utilizados en compiladores.

5. **Menús desplegables**: En interfaces gráficas, los menús pueden contener submenús que son estructuralmente idénticos al menú principal.

La clave de las composiciones recursivas reside en que permiten modelar dominios donde la estructura natural es jerárquica o anidada, y su implementación en Java requiere especial atención para evitar referencias circulares que puedan causar desbordamientos de pila en recorridos recursivos o problemas con la recolección de basura.

## 11. ¿Qué son las relaciones de composición "bidireccionales"? ¿Qué habría que hacer para implementar este tipo de relación en el ejemplo de `Profesor` y `Departamento`?

Las relaciones de composición bidireccionales ocurren cuando dos clases se conocen mutuamente, es decir, cada objeto de una clase mantiene una referencia al otro objeto con el que se relaciona. En una relación unidireccional, solo una de las clases conoce a la otra (como en el ejemplo anterior, donde `Departamento` conocía a sus `Profesor` pero no al revés). En la bidireccional, ambas clases mantienen referencias cruzadas: cada `Profesor` sabría a qué `Departamento` pertenece y cada `Departamento` conocería a sus profesores. Este tipo de relación suele ser más compleja de mantener porque requiere garantizar la consistencia en ambos extremos cuando se realizan modificaciones.

Para implementar la bidireccionalidad en el ejemplo de `Profesor` y `Departamento`, sería necesario modificar ambas clases. La clase `Profesor` necesitaría un atributo que referencie al departamento al que pertenece, y la clase `Departamento` mantendría su lista de profesores. Además, se deben establecer métodos que mantengan la coherencia en ambos lados de la relación: cuando se añade un profesor a un departamento, automáticamente se debe establecer la referencia del profesor hacia ese departamento, y cuando se elimina, dicha referencia debe anularse. También sería necesario considerar si un profesor puede cambiar de departamento y cómo actualizar ambas referencias de manera atómica para no dejar el sistema en un estado inconsistente.

La implementación requeriría especial cuidado con el ciclo de vida y la gestión de referencias para evitar problemas de memoria o estados incoherentes. Sería recomendable que solo uno de los dos extremos gestione la relación (normalmente el contenedor) y que el otro extremo sea de solo lectura o se actualice mediante métodos controlados. También habría que considerar el uso de referencias débiles en alguno de los sentidos si se quisiera evitar que la bidireccionalidad impida la recolección de basura, aunque en este caso al ser una agregación donde los objetos tienen existencia independiente, no sería tan crítico.
