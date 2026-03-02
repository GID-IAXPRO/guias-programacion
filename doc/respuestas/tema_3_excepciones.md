<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Excepciones". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos, Encapsulación.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 3. Excepciones

## 1. Empecemos un tema sobre control de errores en lenguajes de programación, con algo básico. En C, donde no existen las excepciones, pongamos un ejemplo de una raíz que toma número flotante positivo. Queremos controlar el error si la función recibe un número negativo. El usuario debe ser informado pero desde fuera de la función `raiz` ¿Cómo indicamos ese error?. Enumera dos opciones diferentes de diseñar, poniendo un ejemplo de código de cada una.

En el lenguaje C, al carecer de un sistema de excepciones estructurado, el control de errores debe realizarse mediante mecanismos explícitos que permitan comunicar la presencia de un error desde la función al código que la invoca. Dado que la función debe calcular la raíz cuadrada de un número positivo, existen dos enfoques comunes para manejar el caso en que se recibe un argumento negativo.

Una primera opción consiste en utilizar el valor de retorno de la función para indicar el éxito o fracaso de la operación, mientras que el resultado se devuelve a través de un parámetro pasado por referencia. De esta manera, la función retorna un código de error (por ejemplo, un entero donde 0 significa éxito y -1 significa error), y el valor calculado se almacena en una variable cuyo puntero se proporciona como argumento. El siguiente código ilustra esta técnica:

```c
#include <stdio.h>
#include <math.h>

int raiz(double numero, double *resultado) {
    if (numero < 0) {
        return -1;  // Código de error: número negativo
    }
    *resultado = sqrt(numero);
    return 0;  // Éxito
}

int main() {
    double valor;
    if (raiz(-5.0, &valor) == 0) {
        printf("Resultado: %f\n", valor);
    } else {
        printf("Error: no se puede calcular raíz de número negativo\n");
    }
    return 0;
}
```

Una segunda alternativa es utilizar una variable global o un mecanismo similar para almacenar el estado de error, como la variable `errno` que emplea la biblioteca estándar de C. En este diseño, la función retorna el resultado calculado directamente, pero en caso de error se retorna un valor especial (por ejemplo, un NaN o un número que indique situación anómala) y se establece una variable global que el programa principal debe consultar para verificar si ocurrió un error. El siguiente fragmento muestra esta aproximación:

```c
#include <stdio.h>
#include <math.h>
#include <errno.h>

double raiz(double numero) {
    if (numero < 0) {
        errno = EDOM;  // Indicar error de dominio
        return -1.0;   // Valor especial para indicar error
    }else{
            error = 0;
            return sqrt(num);
}
    return sqrt(numero);
}

int main() {
    int error = 0;
    double valor = raiz(-5.0);
    if (errno == EDOM) {
        printf("Error: no se puede calcular raíz de número negativo\n");
    } else {
        printf("Resultado: %f\n", valor);
    }
    return 0;
}
```

Ambos enfoques presentan limitaciones, como la necesidad de verificar explícitamente el error después de cada llamada o el riesgo de ignorar la variable de error, pero son las formas típicas de gestionar situaciones excepcionales en C. Estas carencias motivaron la creación de mecanismos más estructurados en lenguajes posteriores, como las excepciones en Java.


## 2. Brevemente ¿Qué es una **"excepción"**? ¿Con qué objetivo las usa un programador cuando implementa funciones o cuando las llama?

Una **excepción** es un evento anómalo o inesperado que ocurre durante la ejecución de un programa y que interrumpe el flujo normal de instrucciones. Representa una situación excepcional que el código no puede resolver en el contexto donde se produce, como errores de entrada/salida, condiciones de índice fuera de rango, argumentos inválidos o problemas de recursos. En lenguajes como Java, las excepciones son objetos que encapsulan información sobre el error, incluyendo su tipo, un mensaje descriptivo y la traza de la pila de llamadas que permite localizar el punto exacto donde se originó.

Cuando un programador implementa funciones, utiliza excepciones para **separar la lógica principal del tratamiento de errores**, evitando que el código se llene de comprobaciones condicionales que dificulten su lectura y mantenimiento. En lugar de devolver códigos de error que el llamante debe verificar, la función "lanza" una excepción cuando detecta una situación problemática, delegando la responsabilidad de manejar el error en el nivel superior que corresponda. Esto permite que la función exprese claramente su contrato: en condiciones normales devuelve un resultado, pero si algo falla, interrumpe su ejecución y notifica del problema mediante una excepción. Cuando llamamos facilita separar la lógica normal de la de reacción o manejo de la situación errónea.

Por parte de quien llama a una función, el uso de excepciones permite **centralizar y organizar el manejo de errores** en bloques específicos, normalmente mediante estructuras `try-catch`. El programador puede decidir en qué nivel desea capturar cada tipo de excepción, pudiendo ignorar temporalmente algunas para que sean gestionadas más arriba en la pila de llamadas, o bien transformar un tipo de excepción en otro para ofrecer una abstracción más adecuada. Este mecanismo proporciona un flujo de control limpio donde el código que resuelve el problema principal no se mezcla con el código que gestiona las situaciones excepcionales.


## 3. Reescribe el mismo ejemplo de raiz, pero en Java, metiendo ese método en una clase `Calculadora` y llama a dicho método desde el método `main`, mostrando cómo se puede controlar desde fuera.

```java
public class Calculadora {
    public static double raiz(double numero) {
        if (numero < 0) {
            throw new IllegalArgumentException("No se puede calcular raíz de número negativo");
        }
        return Math.sqrt(numero);
    }
    
    public static void main(String[] args) {
        try {
            double resultado = Calculadora.raiz(-5.0);
            System.out.println("Resultado: " + resultado);
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

En este ejemplo, el método `raiz` lanza una excepción de tipo `IllegalArgumentException` cuando recibe un número negativo. La excepción interrumpe inmediatamente la ejecución del método y propaga el error hacia arriba en la pila de llamadas. El objeto excepción contiene un mensaje descriptivo que explica la causa del problema.

Desde el método `main`, la llamada a `raiz` se envuelve en un bloque `try-catch`. Si la ejecución transcurre sin errores, se muestra el resultado. Si se lanza la excepción, el flujo salta al bloque `catch`, donde se captura el objeto excepción y se accede a su mensaje mediante `getMessage()`. De esta forma, el programa puede informar adecuadamente del error sin interrumpir abruptamente su ejecución, manteniendo separada la lógica de cálculo de la gestión de errores.


## 4. ¿Qué es **"lanzar"** una excepción? ¿Qué es **"controlar"** o **"capturar"** una excepción? ¿Qué es que se **"propague"** una excepción? ¿Qué le va ocurriendo a las funciones en la pila de llamadas por donde se va propagando la excepción? ¿Las funciones que no la controlan se reanudan después de alguna forma? Explica con el mismo ejemplo anterior en Java de la raíz cuadrada.

**Lanzar una excepción** es el acto de crear y enviar un objeto excepción desde el punto donde se detecta una situación anómala, interrumpiendo inmediatamente la ejecución normal del método. En el ejemplo, cuando `raiz` recibe un número negativo, ejecuta `throw new IllegalArgumentException(...)`, lo que provoca que el método termine anticipadamente y el control abandone la función, llevando consigo el objeto excepción hacia el lugar desde donde fue invocada.

**Controlar o capturar una excepción** consiste en escribir código específico que pueda manejar la situación excepcional cuando esta se produce. En el ejemplo, el bloque `try-catch` en `main` envuelve la llamada a `raiz`. Si durante la ejecución del `try` se lanza alguna excepción del tipo especificado en el `catch`, el flujo del programa salta inmediatamente a dicho bloque, donde se puede acceder al objeto excepción y tomar las medidas oportunas, como mostrar un mensaje de error.

**Propagación de una excepción** es el proceso por el cual la excepción viaja hacia atrás a través de la pila de llamadas, buscando un manejador que pueda capturarla. Si una función no contiene un bloque `try-catch` que cubra la llamada donde se originó la excepción, esta función termina abruptamente y la excepción se transfiere a la función que la invocó, repitiéndose el proceso.

Las funciones por donde la excepción se propaga **no se reanudan** después de que esta pasa a través de ellas. Cuando una excepción abandona un método, la ejecución de dicho método queda interrumpida permanentemente y ninguna de sus instrucciones posteriores a la línea que causó el error llegará a ejecutarse. El control solo se recupera cuando la excepción encuentra un bloque `catch` adecuado, como ocurre en `main`, donde tras capturar la excepción el programa puede continuar con las instrucciones posteriores al bloque `try-catch`, pero el método `raiz` ya ha finalizado su ejecución de forma anómala.


## 5. ¿Qué ventajas tiene frente a C, la **"propagación natural"** de las excepciones a través de la pila (*stack*) de llamadas?

La principal ventaja de la propagación natural de excepciones frente a los mecanismos de C es que **libera al programador de gestionar explícitamente el error en cada nivel de la jerarquía de llamadas**. En C, si una función detecta un error, debe devolver un código especial o establecer una variable global, y cada función intermedia debe verificar ese resultado y decidir si lo maneja o lo propaga manualmente devolviendo a su vez un código de error. Este enfoque obliga a intercalar comprobaciones condicionales en todo el código, mezclando la lógica principal con el tratamiento de errores y aumentando la probabilidad de que un error se ignore accidentalmente.

Con la propagación automática de excepciones, **las funciones intermedias pueden ignorar completamente la existencia del error** si no tienen la responsabilidad de manejarlo. Una función que llama a `raiz` no necesita comprobar si se produjo un error ni tomar ninguna decisión al respecto; si no captura la excepción, esta simplemente continúa su camino ascendente por la pila. Esto permite que cada función se centre en su cometido principal y que el manejo de errores se concentre únicamente en los niveles donde tiene sentido, normalmente en la interfaz con el usuario o en los puntos de decisión estratégicos de la aplicación.

Además, este mecanismo **preserva automáticamente el contexto del error** a medida que la excepción asciende. El objeto excepción retiene información como el mensaje descriptivo y, fundamentalmente, la traza de la pila (*stack trace*) que muestra exactamente la secuencia de llamadas que condujo al error. Esta información es invaluable para depuración y diagnóstico, ya que permite localizar el origen del problema sin necesidad de que el programador haya instrumentado manualmente el código para transmitir dicha información a través de múltiples niveles.


## 6. En orientación a objetos, ¿las excepciones suelen ser objetos? ¿Qué ventajas tiene esto en términos de encapsulación? ¿Podemos entonces crear excepciones personalizadas?

**Las excepciones son objetos** en lenguajes orientados a objetos como Java. Cada excepción es una instancia de una clase que hereda de `Throwable`, lo que significa que puede contener atributos y métodos que encapsulan información relevante sobre el error. Esta naturaleza orientada a objetos permite que las excepciones transporten no solo un mensaje de texto, sino también datos estructurados, códigos de error específicos, referencias a objetos involucrados en el fallo, o incluso métodos para ayudar en la recuperación del error.

La ventaja en términos de **encapsulación** es que el objeto excepción puede ocultar los detalles internos de cómo se detectó y representó el error, ofreciendo una interfaz pública para acceder a la información relevante. Por ejemplo, una excepción de base de datos podría encapsular el código SQL que falló, el estado de la conexión y el mensaje nativo del motor, pero exponer solo métodos como `getErrorCode()` o `getSQLState()`. Esto permite modificar la implementación interna de la excepción sin afectar al código que la captura, manteniendo el principio de encapsulación.

Sí, es posible y muy recomendable **crear excepciones personalizadas** para representar situaciones de error específicas del dominio de la aplicación. Para ello basta con definir una clase que herede de `Exception` (para excepciones verificadas) o de `RuntimeException` (para no verificadas), y normalmente se implementan varios constructores que delegan en la clase padre. Las excepciones personalizadas permiten expresar semánticamente el tipo de problema ocurrido, como `SaldoInsuficienteException` o `FormatoInvalidoException`, facilitando que quien captura la excepción pueda distinguir diferentes situaciones de error y actuar en consecuencia mediante múltiples bloques `catch`.


## 7. En relación con las ventajas de la encapsulación, comparando el ejemplo en C con Java. ¿Qué **información esencial** lleva cualquier **objeto excepción** que es muy útil tener cuando se llega a un manejador?

Cualquier objeto excepción en Java encapsula información esencial que resulta de gran utilidad cuando el error llega al manejador. La más relevante es la **traza de la pila** (*stack trace*), que contiene el listado completo de las llamadas a métodos desde el punto donde se lanzó la excepción hasta el lugar donde se captura, incluyendo los nombres de las clases, métodos y números de línea. Esta información, accesible mediante métodos como `printStackTrace()` o `getStackTrace()`, permite reconstruir exactamente el camino de ejecución que condujo al error, algo que en C requeriría instrumentar manualmente cada función para transmitir el contexto.

Además de la traza, todo objeto excepción incluye un **mensaje descriptivo** que se establece en el momento de su creación, normalmente proporcionado como argumento al constructor. Este mensaje, recuperable mediante `getMessage()`, debe contener una explicación legible de la causa del error, como "No se puede calcular raíz de número negativo". Opcionalmente, las excepciones pueden encapsular una **causa subyacente** (*cause*), que es otra excepción que originó la actual, permitiendo construir cadenas de errores donde una excepción de más bajo nivel es la raíz del problema.

Esta información viaja automáticamente con la excepción a través de la pila de llamadas sin que el programador tenga que hacer nada para propagarla. Cuando el error llega al manejador, este dispone de todos los datos necesarios para tomar decisiones informadas: mostrar un mensaje adecuado al usuario, registrar el error en un archivo de log con todo el contexto, o incluso intentar una estrategia de recuperación basada en el tipo específico de excepción y la información que transporta. En C, lograr esto requeriría que cada función construyera y transmitiera estructuras de datos complejas manualmente, con el consiguiente riesgo de pérdida de información.


## 8. En Java, sobre el bloque **"try-catch"**, ¿se pueden tener más de un bloque `catch`? ¿cuántos bloques `catch` se ejecutan?

En Java, un bloque `try` puede tener múltiples bloques `catch` asociados, cada uno especializado en capturar un tipo diferente de excepción. Esta estructura permite organizar el manejo de errores de forma granular, donde cada bloque `catch` contiene el código específico para tratar una determinada situación excepcional. La sintaxis requiere que los bloques `catch` aparezcan consecutivamente después del bloque `try`, y es importante ordenarlos desde el tipo más específico al más general, ya que el primer bloque compatible con la excepción lanzada será el único que se ejecutará.

De todos los bloques `catch` definidos, **solo se ejecuta un único bloque**, aquel cuyo parámetro coincida con el tipo de la excepción lanzada o sea uno de sus supertipos. Una vez que la excepción es capturada por un bloque `catch`, el flujo de ejecución continúa por ese bloque y, al finalizar, salta a la instrucción siguiente al último bloque `catch`, sin evaluar ninguno de los bloques restantes. Este comportamiento asegura que cada excepción sea manejada por el código más adecuado según su tipo, evitando duplicidades o conflictos en el tratamiento del error.

El siguiente ejemplo ilustra múltiples bloques `catch`:

```java
try {
    double resultado = Calculadora.raiz(-5.0);
} catch (IllegalArgumentException e) {
    System.out.println("Error de argumento: " + e.getMessage());
} catch (ArithmeticException e) {
    System.out.println("Error aritmético: " + e.getMessage());
} catch (RuntimeException e) {
    System.out.println("Error en tiempo de ejecución: " + e.getMessage());
}
```

En este código, si se lanza una `IllegalArgumentException`, se ejecuta el primer bloque `catch` y los restantes se ignoran completamente. Si se lanzara otro tipo de excepción no contemplada específicamente pero que herede de `RuntimeException`, se ejecutaría el último bloque por ser el más general. Esta jerarquía de captura proporciona flexibilidad para manejar errores con distintos niveles de especificidad.


## 9. Si las excepciones producen rupturas en el código llamador, ¿cómo podemos garantizar que se ejecuta siempre finalmente un código necesario para cierre de ficheros, liberacion de recursos, antes de que continúe propagándose la excepción? Pon un ejemplo en Java con `finally`, tanto con `catch` como sin él.

El bloque `finally` en Java permite garantizar la ejecución de código necesario independientemente de lo que ocurra en el bloque `try`, ya sea que este finalice normalmente o que se lance una excepción. Este bloque se ejecuta siempre, incluso si hay una instrucción `return` en el `try` o en el `catch`, y su objetivo principal es liberar recursos, cerrar conexiones o realizar cualquier tarea de limpieza que deba ocurrir antes de que el flujo de control abandone la estructura. El bloque `finally` es opcional y puede colocarse después de los bloques `catch` o directamente después del `try` si no hay bloques `catch`.

En el siguiente ejemplo se muestra el uso de `finally` junto con un bloque `catch` para garantizar el cierre de un fichero, independientemente de si la operación de lectura se realiza correctamente o se produce una excepción:

```java
import java.io.*;

public class EjemploFinally {
    public static void leerFichero(String nombre) {
        BufferedReader lector = null;
        try {
            lector = new BufferedReader(new FileReader(nombre));
            String linea = lector.readLine();
            System.out.println("Contenido: " + linea);
        } catch (FileNotFoundException e) {
            System.out.println("Error: archivo no encontrado");
        } catch (IOException e) {
            System.out.println("Error de lectura");
        } finally {
            try {
                if (lector != null) {
                    lector.close();
                    System.out.println("Fichero cerrado correctamente");
                }
            } catch (IOException e) {
                System.out.println("Error al cerrar el fichero");
            }
        }
    }
}
```

El bloque `finally` también puede utilizarse sin bloques `catch`, cuando se desea que la excepción se propague pero asegurando que se ejecute código de limpieza antes de que esto ocurra. En este caso, la excepción no se captura en el método, por lo que continúa propagándose después de ejecutarse el `finally`:

```java
public static void metodoConFinally() throws IOException {
    BufferedReader lector = null;
    try {
        lector = new BufferedReader(new FileReader("datos.txt"));
        String linea = lector.readLine();
        System.out.println("Primera línea: " + linea);
    } finally {
        if (lector != null) {
            try {
                lector.close();
                System.out.println("Recurso liberado en finally");
            } catch (IOException e) {
                System.out.println("Error al cerrar");
            }
        }
    }
    // El código aquí solo se ejecuta si no hay excepción
}
```

En este segundo ejemplo, si se produce una `FileNotFoundException` al abrir el fichero, la excepción se lanzará inmediatamente, pero antes de que el método termine y la excepción se propague al llamante, se ejecutará el bloque `finally`, asegurando que cualquier recurso que se hubiera abierto parcialmente quede correctamente liberado. Esta garantía de ejecución hace que `finally` sea la herramienta adecuada para tareas de limpieza que deben ocurrir en cualquier escenario.


## 10. En Java, el bloque `finally` puede ir sin `catch`? ¿Se ejecuta siempre tanto si ocurre como si no ocurre una excepción? ¿Y si hay un `return` en medio del `try`?

**Sí, el bloque `finally` puede utilizarse sin `catch`** en Java. Esta estructura es perfectamente válida y tiene su utilidad cuando se desea garantizar la ejecución de código de limpieza pero no se quiere capturar la excepción en el mismo método, permitiendo que esta se propague hacia arriba en la pila de llamadas. En este caso, el bloque `try` va seguido directamente del bloque `finally`, sin ningún bloque `catch` intermedio, y el método debe declarar las excepciones que puede lanzar mediante la cláusula `throws`.

**El bloque `finally` se ejecuta siempre**, independientemente de lo que ocurra en el bloque `try`. Tanto si la ejecución del `try` transcurre sin errores como si se lanza una excepción, el código contenido en `finally` se ejecutará antes de que el control abandone la estructura. Esta característica lo convierte en el lugar idóneo para liberar recursos como ficheros, conexiones de red o bloqueos, asegurando que dicha liberación ocurra en cualquier circunstancia.

**Incluso si hay una instrucción `return` dentro del bloque `try`, el bloque `finally` se ejecuta antes de que el valor sea devuelto**. La presencia de un `return` no impide la ejecución de `finally`; de hecho, el flujo de ejecución primero completa el bloque `finally` y solo entonces retorna el valor. Esto significa que cualquier modificación de variables en `finally` puede afectar al valor que finalmente se retorna, aunque se considera una mala práctica depender de este comportamiento. El siguiente ejemplo ilustra esta situación:

```java
public class EjemploReturnFinally {
    public static int probarFinally() {
        try {
            System.out.println("Dentro del try");
            return 1; // Este return no impide que se ejecute finally
        } finally {
            System.out.println("Esto se ejecuta SIEMPRE, incluso antes del return");
            // Código de limpieza aquí
        }
    }
    
    public static void main(String[] args) {
        System.out.println("Resultado: " + probarFinally());
    }
}
```

La ejecución de este código mostrará primero "Dentro del try", después "Esto se ejecuta SIEMPRE, incluso antes del return", y finalmente "Resultado: 1". Esta garantía de ejecución hace que `finally` sea un mecanismo fiable para tareas de limpieza, incluso en situaciones donde el flujo normal del programa incluye retornos anticipados.


## 11. En Java, qué son las excepciones **"controladas"** y las **"no controladas"**? ¿Qué papel juega `RuntimeException`? Pon un ejemplo de excepciones típicas controladas y no controladas que incluso nosotros mismos podríamos usar. Haz dos listas con 3 o 4 ejemplos de situación donde se suele preferir una excepción controlada y donde se suele preferir una excepción no controlada.

En Java, las excepciones se clasifican en dos categorías principales: **controladas** (*checked exceptions*) y **no controladas** (*unchecked exceptions*). Las excepciones controladas son aquellas que el compilador obliga a manejar explícitamente, bien mediante un bloque `try-catch` o bien declarándolas en la cláusula `throws` del método que puede generarlas. Por el contrario, las excepciones no controladas no están sujetas a esta verificación en tiempo de compilación; el programador puede manejarlas si lo desea, pero no está obligado a hacerlo.

**`RuntimeException`** y todas sus subclases constituyen el núcleo de las excepciones no controladas. Esta clase hereda de `Exception`, pero el compilador trata de forma especial a toda la jerarquía que desciende de `RuntimeException`, eximiendo al programador de la obligación de declararlas o capturarlas. Las excepciones que heredan directamente de `Exception` sin pasar por `RuntimeException` son controladas. Esta distinción refleja la filosofía de que ciertos errores, como los de programación, deberían poder prevenirse y no es razonable forzar su manejo en cada llamada.

**Ejemplos de excepciones controladas típicas:**
- `IOException`: errores de entrada/salida al trabajar con ficheros
- `SQLException`: problemas en operaciones con bases de datos
- `ClassNotFoundException`: cuando no se encuentra una clase solicitada
- `FileNotFoundException`: caso particular de IOException al abrir un archivo inexistente

**Ejemplos de excepciones no controladas típicas:**
- `NullPointerException`: al intentar acceder a un objeto con referencia nula
- `IllegalArgumentException`: cuando se pasa un argumento inválido a un método
- `IndexOutOfBoundsException`: al acceder a una posición fuera de los límites de un array
- `ArithmeticException`: errores aritméticos como división por cero

**Situaciones donde se suele preferir una excepción controlada:**

1. **Operaciones con recursos externos**: al abrir un fichero, conectar a una base de datos o acceder a un servicio de red, donde los fallos son previsibles y deben ser gestionados.
2. **Validación de entrada en APIs públicas**: cuando se diseña una biblioteca y se espera que el llamante pueda recuperarse de ciertos errores.
3. **Procesos que requieren confirmación transaccional**: en operaciones que deben poder deshacerse si algo falla.
4. **Condiciones que el llamante puede anticipar y resolver**: como intentar leer un archivo que puede no existir, donde se puede pedir otro nombre al usuario.

**Situaciones donde se suele preferir una excepción no controlada:**

1. **Errores de programación**: como pasar un índice fuera de rango o no inicializar un objeto, situaciones que deberían corregirse en el código.
2. **Precondiciones violadas**: cuando un método recibe parámetros que incumplen su contrato, como un valor negativo donde no tiene sentido.
3. **Fallas internas del sistema**: errores de los que no se puede recuperar significativamente en tiempo de ejecución.
4. **Casos donde el manejo obligatorio entorpecería la claridad del código**: si forzar a capturar la excepción en cada llamada haría el código ilegible, como ocurriría con `NullPointerException` si fuera controlada.


## 12. ¿Qué es y para qué se usa `throws`? ¿Por qué es alternativa a capturar una excepción controlada?

**`throws` es una cláusula que se utiliza en la declaración de un método para indicar que dicho método puede lanzar uno o varios tipos de excepciones controladas** durante su ejecución, y que no las capturará internamente, delegando la responsabilidad de manejarlas en el código que lo invoque. La sintaxis consiste en añadir la palabra reservada `throws` seguida de la lista de excepciones separadas por comas después de la lista de parámetros del método. Esta declaración forma parte del contrato del método, informando explícitamente a quien lo llama de las situaciones excepcionales que debe prever.

Esta cláusula constituye una alternativa a capturar la excepción porque **permite posponer el manejo del error a un nivel superior de la pila de llamadas**. Cuando un método encuentra una situación que generaría una excepción controlada, tiene dos opciones: rodear el código problemático con un bloque `try-catch` y resolver el error en ese mismo nivel, o bien declarar la excepción con `throws` para que el método que lo ha invocado asuma la responsabilidad. Esta decisión permite diseñar una arquitectura donde los errores se manejan en los niveles más apropiados, normalmente donde se dispone del contexto necesario para tomar decisiones sobre cómo recuperarse.

La diferencia fundamental entre usar `throws` y capturar la excepción es el **momento y lugar donde se gestiona el error**. Con `try-catch`, el método actual asume el control y decide cómo responder ante la falla. Con `throws`, el método actual renuncia a manejar el error y lo transfiere hacia arriba, obligando a los métodos llamantes a declarar también `throws` o a capturarlo eventualmente. Por ejemplo, un método de bajo nivel que accede a un fichero puede declarar `throws IOException`, permitiendo que sea el método de negocio que lo utiliza quien decida si muestra un mensaje al usuario, reintenta la operación o propaga el error más arriba. Esta propagación controlada es precisamente la ventaja que ofrecen las excepciones frente a los códigos de error de C.


## 13. Pon un ejemplo en Java de firma de método que incluya `throws`, de una función que abre un fichero pero que declara que no le interesa menejar la excepción de si el fichero no existe, sino que se propague hacia arriba. Eso sí, acuérdate del `finally`.

```java
import java.io.*;

public class LectorFicheros {
    
    public String leerPrimeraLinea(String nombreFichero) throws IOException {
        BufferedReader lector = null;
        try {
            lector = new BufferedReader(new FileReader(nombreFichero));
            return lector.readLine();
        } finally {
            if (lector != null) {
                try {
                    lector.close();
                } catch (IOException e) {
                    System.err.println("Error al cerrar el fichero: " + e.getMessage());
                }
            }
        }
    }
}
```

En este ejemplo, el método `leerPrimeraLinea` declara explícitamente `throws IOException` en su firma. Esto indica que el método no capturará las posibles excepciones de entrada/salida que puedan ocurrir, como `FileNotFoundException` si el archivo no existe o `IOException` durante la lectura, sino que las propagará hacia el método que lo invocó. La cláusula `throws` forma parte del contrato del método y obliga a quien llame a `leerPrimeraLinea` a manejar estas excepciones, bien capturándolas con `try-catch` o declarando a su vez `throws` para seguir propagándolas.

El bloque `try` contiene la operación que puede lanzar excepciones: la creación del `FileReader` y la lectura de la primera línea. Si ocurre una excepción en cualquiera de estas operaciones, la ejecución salta inmediatamente al bloque `finally` antes de que la excepción abandone el método. El bloque `finally` garantiza que el recurso `BufferedReader` se cierre correctamente, independientemente de si la operación tuvo éxito o falló. Dentro del `finally` se incluye un segundo `try-catch` para manejar posibles errores durante el cierre, pero estos no interfieren con la excepción original que se está propagando.

De esta forma, el método combina la propagación de la excepción controlada (mediante `throws`) con la liberación segura de recursos (mediante `finally`). El llamante recibirá la excepción original y podrá decidir cómo manejarla, mientras que el recurso queda liberado en cualquier escenario.


## 14. ¿Podemos poner en `throws` excepciones no controladas, como `RuntimeException`? ¿Debería el método llamador entonces poner `try-catch` en ese caso? ¿Qué sentido tendría?

**Sí, es posible incluir excepciones no controladas como `RuntimeException` en la cláusula `throws`** de un método, aunque no es obligatorio y resulta poco frecuente. Java permite declarar cualquier tipo de excepción en `throws`, tanto controladas como no controladas, y la sintaxis es perfectamente válida. Sin embargo, incluir excepciones no controladas en `throws` tiene un valor puramente documental, ya que el compilador no obliga a los métodos llamantes a manejar estas excepciones ni a declararlas a su vez.

El método llamador **no está obligado a capturar con `try-catch` las excepciones no controladas** que aparecen en la cláusula `throws` del método al que invoca. Dado que las excepciones no controladas no están sujetas a la verificación en tiempo de compilación, el programador puede decidir ignorarlas completamente o capturarlas si lo considera necesario, pero no existe ninguna imposición del compilador. Esto contrasta con las excepciones controladas, donde la presencia en `throws` exige una acción por parte del llamante.

El **sentido de declarar excepciones no controladas en `throws`** es puramente informativo y de documentación. Sirve para comunicar explícitamente a quienes utilicen el método que, aunque no estén obligados a hacerlo, podría ser recomendable capturar ciertas excepciones en determinados contextos. Por ejemplo, un método que realiza operaciones aritméticas podría declarar `throws ArithmeticException` para documentar que puede lanzar esa excepción en caso de división por cero, aunque el llamante no tenga ninguna obligación de capturarla. Esta práctica se considera poco común y en general se prefiere documentar estas situaciones en los comentarios del método mediante anotaciones como `@throws` en Javadoc, que cumplen la misma función informativa sin añadir ruido a la firma del método.


## 15. ¿Cuándo se recomienda usar excepciones controladas, como `IOException`, y cuándo no controladas como `IllegalArgumentException`? ¿Existen en todos los lenguajes ambas opciones? En los que sólo existe una opción, ¿cuál es la más habitual?

**Las excepciones controladas se recomiendan para situaciones donde el llamante puede recuperarse razonablemente del error** y donde es importante que el programador no olvide considerar esa posibilidad. Son apropiadas para errores relacionados con condiciones externas previsibles, como problemas de entrada/salida, errores de red, falta de archivos o fallos en bases de datos. En estos casos, el programa puede tener alternativas: pedir otro nombre de archivo, reintentar la conexión, o mostrar un mensaje al usuario. La obligación impuesta por el compilador de manejar estas excepciones garantiza que el programador tome una decisión consciente sobre cómo responder ante estas situaciones.

**Las excepciones no controladas se recomiendan para errores que reflejan problemas de programación o condiciones que no deberían ocurrir** si el código está correctamente implementado. `IllegalArgumentException`, `NullPointerException` o `IndexOutOfBoundsException` son ejemplos típicos: indican que el método ha sido invocado con argumentos que violan su contrato. Forzar a capturar estas excepciones en cada llamada entorpecería la legibilidad del código sin aportar valor, ya que la solución no está en el manejo en tiempo de ejecución sino en corregir el código que causa el error. También son adecuadas para fallos internos de los que no es posible recuperarse significativamente.

**No todos los lenguajes ofrecen ambas opciones**. Esta distinción entre controladas y no controladas es una característica particular de Java y algunos lenguajes que han adoptado su modelo. Lenguajes como C++, Python, JavaScript, C# o Ruby solo disponen de excepciones no controladas, donde no existe verificación en tiempo de compilación sobre su manejo. En estos lenguajes, todas las excepciones se comportan como las no controladas de Java: pueden capturarse opcionalmente pero no hay obligación de hacerlo.

**En los lenguajes que solo ofrecen una opción, la más habitual es el modelo de excepciones no controladas**. Esta aproximación resulta más simple y flexible, delegando completamente en el programador la responsabilidad de decidir qué excepciones capturar y cuáles dejar propagar. La experiencia con Java ha mostrado que el uso excesivo de excepciones controladas puede llevar a código con bloques `try-catch` vacíos o a una propagación generalizada mediante `throws` que acaba siendo contraproducente, razón por la que muchos lenguajes posteriores han optado por el modelo no controlado o por sistemas híbridos más permisivos.


## 16. ¿Tiene sentido lanzar excepciones dentro del `catch`? ¿Se puede relanzar la misma excepción capturada? ¿Cuándo tendría sentido hacer esto último? Pon ejemplos de ambos casos.

**Sí, tiene perfecto sentido lanzar excepciones dentro de un bloque `catch`**, y es una práctica común en el manejo de errores. Esta técnica permite transformar un tipo de excepción en otro más apropiado para el nivel de abstracción actual, o bien realizar alguna acción antes de propagar la excepción original. Al lanzar una nueva excepción dentro del `catch`, la excepción original puede encapsularse como causa de la nueva, preservando así la información completa del error para facilitar la depuración. Esta estrategia es especialmente útil en diseños por capas, donde una excepción de bajo nivel como `SQLException` se convierte en una excepción de negocio como `AccesoDatosException`.

**Es posible relanzar la misma excepción que se acaba de capturar** utilizando la palabra clave `throw` seguida de la referencia a la excepción capturada. Esta operación no crea una nueva excepción, sino que vuelve a lanzar exactamente el mismo objeto, manteniendo intacta toda su información original, incluyendo la traza de pila. El siguiente ejemplo muestra cómo relanzar la misma excepción después de registrar su ocurrencia:

```java
public void procesarArchivo(String nombre) throws IOException {
    try {
        BufferedReader lector = new BufferedReader(new FileReader(nombre));
        // Procesar el archivo...
    } catch (IOException e) {
        System.err.println("Error al procesar archivo: " + e.getMessage());
        // Registrar en log antes de relanzar
        throw e; // Se relanza la misma excepción
    }
}
```

**El relanzamiento de la misma excepción tiene sentido cuando se necesita realizar alguna acción antes de que la excepción continúe propagándose**, pero sin modificar su naturaleza ni perder información. Los casos más habituales incluyen el registro en un archivo de log, la liberación parcial de recursos, la notificación a otros componentes, o simplemente la decisión de que el nivel actual no tiene suficiente contexto para manejar el error pero sí puede aportar información adicional mediante el registro. Esta técnica permite que la excepción mantenga su traza original mientras se ejecuta código de limpieza o monitorización en el nivel intermedio.

**Ejemplo de transformación de excepción encapsulando la original:**

```java
public void actualizarCliente(Cliente cliente) throws ServicioException {
    try {
        repositorio.guardar(cliente);
    } catch (SQLException e) {
        // Se lanza una nueva excepción que encapsula la original
        throw new ServicioException("Error al guardar el cliente", e);
    }
}
```

En este caso, la excepción original `SQLException` queda disponible mediante el método `getCause()` de la nueva excepción, permitiendo que niveles superiores accedan tanto al error de negocio como al detalle técnico subyacente. Esta práctica mantiene la trazabilidad completa del error mientras se adapta al vocabulario de la capa actual.


## 17. ¿En qué consiste que una excepción sea la **"causa"** de otra excepción? Pon un ejemplo en Java, donde capturemos una excepción de bajo nivel y la encapsulemos en otra personalizada de alto nivel. Cuando una excepción sale por pantalla y tiene una causa, ¿se ve?

**Una excepción actúa como "causa" de otra cuando se encapsula una excepción original dentro de una nueva excepción**, estableciendo una relación que permite preservar la traza completa del error a través de diferentes capas de abstracción. Este mecanismo es fundamental en diseños multicapa, donde las excepciones de bajo nivel (como `SQLException` o `IOException`) se transforman en excepciones de negocio más significativas sin perder la información técnica original. La causa se almacena internamente en la nueva excepción y puede recuperarse posteriormente mediante el método `getCause()`, manteniendo así la cadena completa de errores que condujeron al fallo.

**Ejemplo de encapsulación de una excepción de bajo nivel en una personalizada**:

```java
// Excepción personalizada de alto nivel
class ServicioException extends Exception {
    public ServicioException(String mensaje, Throwable causa) {
        super(mensaje, causa);
    }
}

public class ServicioClientes {
    public void actualizarCliente(Cliente cliente) throws ServicioException {
        try {
            // Operación que puede lanzar SQLException
            repositorio.guardar(cliente);
        } catch (SQLException e) {
            // Se encapsula SQLException como causa de ServicioException
            throw new ServicioException("Error al actualizar cliente en base de datos", e);
        }
    }
}
```

**Cuando una excepción que tiene una causa se muestra por pantalla, la información de la causa sí es visible**. Tanto si se imprime la excepción directamente con `printStackTrace()` como si se muestra su representación mediante `toString()`, la salida incluirá la cadena completa de excepciones, mostrando tanto el mensaje de la excepción de alto nivel como el de la excepción original y su traza de pila. Esto permite a quien depura el programa seguir el rastro del error desde el punto donde se detectó hasta su origen real.

Por ejemplo, al ejecutar el código anterior y capturar la excepción en un nivel superior para mostrarla:

```java
try {
    servicio.actualizarCliente(cliente);
} catch (ServicioException e) {
    e.printStackTrace();  // Muestra tanto ServicioException como su causa SQLException
}
```

La salida por consola mostrará algo similar a:

```
ServicioException: Error al actualizar cliente en base de datos
    at ServicioClientes.actualizarCliente(ServicioClientes.java:15)
    at Main.main(Main.java:8)
Caused by: java.sql.SQLException: Error de sintaxis en SQL
    at Repositorio.guardar(Repositorio.java:42)
    at ServicioClientes.actualizarCliente(ServicioClientes.java:12)
    ... 1 more
```

Esta visualización con el "Caused by" es extremadamente útil para entender la secuencia completa de errores y localizar rápidamente el origen del problema, ya que muestra explícitamente la relación causal entre las diferentes excepciones que se han ido encapsulando.
