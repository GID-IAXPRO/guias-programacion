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

### Respuesta
Una forma clara y portable es separar “resultado” de “estado”: la función devuelve un código de estado (éxito/fracaso) y entrega el valor por parámetro de salida. Así, el caller decide cómo informar al usuario desde fuera de raiz. Esta estrategia evita ambigüedades con valores especiales (p. ej., -1, NaN) y funciona igual en entornos sin soporte de NAN

int raiz(double x, double *out) {
    if (x < 0.0) return 0;           // 0 = error
    if (out == NULL) return 0;       // defensa básica
    *out = sqrt(x);
    return 1;                        // 1 = ok
}

int main(void) {
    double r;
    if (raiz(9.0, &r)) {
        printf("raiz = %.3f\n", r);
    } else {
        printf("Error: la entrada no puede ser negativa.\n");
    }
}


Otra opción es empaquetar valor y estado en una estructura; la función devuelve esa estructura y el caller inspecciona el indicador de validez. Este diseño es ergonómico cuando se desea retornar “un solo objeto” sin parámetros de salida y deja espacio para ampliar metadatos de error (códigos, mensajes) sin cambiar la firma


typedef struct {
    int ok;         // 1 = éxito, 0 = error
    double value;   // válido solo si ok == 1
} RaizResult;

RaizResult raiz(double x) {
    if (x < 0.0)   return (RaizResult){ .ok = 0, .value = 0.0 };
    return (RaizResult){ .ok = 1, .value = sqrt(x) };
}

int main(void) {
    RaizResult a = raiz(16.0);
    if (a.ok) printf("raiz = %.3f\n", a.value);
    else      printf("Error: la entrada no puede ser negativa.\n");
}



## 2. Brevemente ¿Qué es una **"excepción"**? ¿Con qué objetivo las usa un programador cuando implementa funciones o cuando las llama?

### Respuesta

Una excepción es un mecanismo que permite indicar que durante la ejecución de un programa ha ocurrido una situación anómala o inesperada, distinta del flujo normal. Esta“interrumpe” el flujo normal y transfiere el control a un manejador específico.

El objetivo principal al usarlas al implementar funciones es señalar problemas que impiden completar correctamente la operación: datos inválidos, estados incoherentes, falta de recursos, etc

Por otro lado, al llamar funciones, las excepciones permiten tratar los errores de forma estructurada y localizada. En lugar de comprobar manualmente cada posible código de error, el programador puede colocar un bloque try y capturar solo los problemas que le interesa gestionar


## 3. Reescribe el mismo ejemplo de raiz, pero en Java, metiendo ese método en una clase `Calculadora` y llama a dicho método desde el método `main`, mostrando cómo se puede controlar desde fuera.


### Respuesta

En Java puede modelarse el caso “entrada negativa” como una condición excepcional usando throw. En lugar de devolver un código de error, el método raiz valida el argumento y, si es inválido, lanza una IllegalArgumentException (excepción no comprobada adecuada para argumentos erróneos). De este modo, el método mantiene su contrato: “o devuelve la raíz cuadrada para entradas válidas, o comunica el fallo lanzando una excepción”

public class Calculadora {

    public static double raiz(double x) {
        if (x < 0.0) {
            throw new IllegalArgumentException("La entrada no puede ser negativa: " + x);
        }
        return Math.sqrt(x);
    }
}
public static void main(String[] args) {
    
    try {
            double r2 = Calculadora.raiz(-4.0);
            System.out.printf("raiz(-4.0) = %.3f%n", r2);
        } 
        catch (IllegalArgumentException e) {
            // Aquí se informa al usuario desde fuera de 'raiz'
            System.out.println("Error: " + e.getMessage());
        }
}

asasasassasassas


## 4. ¿Qué es **"lanzar"** una excepción? ¿Qué es **"controlar"** o **"capturar"** una excepción? ¿Qué es que se **"propague"** una excepción? ¿Qué le va ocurriendo a las funciones en la pila de llamadas por donde se va propagando la excepción? ¿Las funciones que no la controlan se reanudan después de alguna forma? Explica con el mismo ejemplo anterior en Java de la raíz cuadrada.

### Respuesta
Al lanzar una excepción se indica que, dentro de una función, ha ocurrido una situación anómala que impide continuar el flujo normal. En Java esto se expresa con throw. Cuando se lanza una excepción, la ejecución abandona inmediatamente la función en el punto exacto del throw

Controlar o capturar una excepción consiste en envolver el código que podría fallar dentro de un bloque try y, a continuación, escribir uno o varios bloques catch para interceptarla. El bloque catch es el encargado de decidir qué hacer: mostrar un mensaje, recuperar el fallo, devolver un valor alternativo, etc

Cuando una excepción no es capturada en una función, esta se propaga hacia atrás por la pila de llamadas. Esto significa que la función que lanzó la excepción finaliza abruptamente, la función que la llamó también finaliza si no tiene un catch, y así sucesivamente

En la propagación, las funciones por las que pasa la excepción van “desapilándose” y perdiendo la oportunidad de completar su ejecución normal. No existen reanudaciones posteriores: una vez que una función ha sido abandonada por una excepción no capturada, no vuelve a retomarse. Esto contrasta con C, donde la función devolvería un valor y el programa seguiría normalmente


## 5. ¿Qué ventajas tiene frente a C, la **"propagación natural"** de las excepciones a través de la pila (*stack*) de llamadas?

### Respuesta
La propagación natural de las excepciones en Java aporta una forma estructurada y automática de comunicar errores a través de múltiples niveles de funciones, algo que en C debe hacerse manualmente

Otra ventaja es la claridad y separación del código normal frente al código de manejo de errores. En Java el bloque try contiene la lógica principal, y los bloques catch agrupan el tratamiento de errores. En C, las comprobaciones están intercaladas línea a línea con la lógica normal, lo que dificulta leer el flujo real del programa

Además, la propagación evita errores silenciosos muy comunes en C, donde un desarrollador puede olvidar comprobar un código de error y continuar sin darse cuenta. En Java, si una excepción no es capturada, la excepción sigue subiendo por la pila y fuerza a tratarla o a que el programa finalice mostrando un error claro

Finalmente, la propagación permite manejar errores en un nivel más alto donde existe una mejor visión del contexto




## 6. En orientación a objetos, ¿las excepciones suelen ser objetos? ¿Qué ventajas tiene esto en términos de encapsulación? ¿Podemos entonces crear excepciones personalizadas?

### Respuesta

En orientación a objetos, las excepciones sí suelen ser objetos, y en Java todas derivan de la clase base Throwable. Al ser objetos, llevan consigo información encapsulada: un mensaje descriptivo, la causa interna del error, e incluso la traza de pila. Esto permite que la excepción represente qué ocurrió, sino también qué tipo de problema es y qué datos útiles se asocian a él
Esto evita dispersar la información del error por múltiples variables y facilita que el código pueda consultar la excepción mediante (getMessage(), getCause(), etc.) 

Es posible crear excepciones personalizadas simplemente extendiendo Exception o RuntimeException

public class EntradaNegativaException extends RuntimeException {
    public EntradaNegativaException(String msg) {
        super(msg);
    }
}

## 7. En relación con las ventajas de la encapsulación, comparando el ejemplo en C con Java. ¿Qué **información esencial** lleva cualquier **objeto excepción** que es muy útil tener cuando se llega a un manejador?

### Respuesta
En una excepción en Java se encapsula información esencial que el manejador recibe automáticamente, sin necesidad de que todas las funciones intermedias la transmitan manualmente (como ocurriría en C). La pieza más importante es el mensaje descriptivo (getMessage()), que explica la causa del error con un texto significativo

Además, cualquier objeto excepción incluye la traza de la pila (stack trace), que detalla exactamente por qué métodos pasó la ejecución hasta llegar al punto donde se lanzó el error. En C, esta información no se obtiene de forma automática.

También forma parte de la excepción la causa encadenada (getCause()), que permite indicar otra excepción que originó el error actual. Esto es muy útil cuando se encapsulan fallos de niveles inferiores (por ejemplo, errores de E/S o de parseo) dentro de excepciones de nivel más alto

## 8. En Java, sobre el bloque **"try-catch"**, ¿se pueden tener más de un bloque `catch`? ¿cuántos bloques `catch` se ejecutan?

### Respuesta
Es posible colocar varios bloques catch después de un mismo bloque try. Cada bloque catch se asocia a un tipo concreto de excepción (o a una jerarquía de tipos), y esto permite reaccionar de manera diferente según el tipo exacto del problema que se haya producido. Sin embargo; solo se ejecuta uno. En el momento en que se produce una excepción dentro del try, Java busca el primer catch compatible con el tipo de la excepción, se ejecuta y se ignoran los posteriores
El orden de los catch es importante: los más específicos deben colocarse antes que los más generales


## 9. Si las excepciones producen rupturas en el código llamador, ¿cómo podemos garantizar que se ejecuta siempre finalmente un código necesario para cierre de ficheros, liberacion de recursos, antes de que continúe propagándose la excepción? Pon un ejemplo en Java con `finally`, tanto con `catch` como sin él.

### Respuesta
En Java, cuando una excepción rompe el flujo normal del método, puede garantizarse la ejecución de cierto código indispensable —como liberar recursos, cerrar ficheros o desconectar conexiones— utilizando el bloque finally. Este bloque siempre se ejecuta, ocurra o no una excepción, exista o no un bloque catch. Solo después de terminar finally, la excepción continúa propagándose si no fue capturada

public static void ejemploConCatch() {
    java.io.FileReader fr = null;
    try {
        fr = new java.io.FileReader("datos.txt");
        // Uso del recurso
        int x = Calculadora.raiz(-4);  // Lanza excepción
        System.out.println(x);
    } catch (IllegalArgumentException e) {
        System.out.println("Error capturado: " + e.getMessage());
    } finally {
        // Código que SIEMPRE se ejecuta
        if (fr != null) {
            try { fr.close(); } catch (Exception ignored) {}
        }
        System.out.println("finally ejecutado (con catch).");
    }
}


## 10. En Java, el bloque `finally` puede ir sin `catch`? ¿Se ejecuta siempre tanto si ocurre como si no ocurre una excepción? ¿Y si hay un `return` en medio del `try`?

### Respuesta
En Java el bloque finally puede ir sin catch.El bloque finally se ejecuta siempre, tanto si ocurre una excepción como si no. En caso de que se lance una excepción dentro del try y no haya ningún catch, la excepción se propagará igualmente, pero solo después de que se ejecute el finally

public static int ejemploReturn() {
    try {
        System.out.println("Dentro de try");
        return 10; // return adelantado
    } finally {
        System.out.println("finally SIEMPRE se ejecuta");
    }
}

En un try, debe existir al menos un catch o un finally.


dsadassdasd

## 11. En Java, qué son las excepciones **"controladas"** y las **"no controladas"**? ¿Qué papel juega `RuntimeException`? Pon un ejemplo de excepciones típicas controladas y no controladas que incluso nosotros mismos podríamos usar. Haz dos listas con 3 o 4 ejemplos de situación donde se suele preferir una excepción controlada y donde se suele preferir una excepción no controlada.

### Respuesta


## 12. ¿Qué es y para qué se usa `throws`? ¿Por qué es alternativa a capturar una excepción controlada?

### Respuesta


## 13. Pon un ejemplo en Java de firma de método que incluya `throws`, de una función que abre un fichero pero que declara que no le interesa menejar la excepción de si el fichero no existe, sino que se propague hacia arriba. Eso sí, acuérdate del `finally`.

### Respuesta


## 14. ¿Podemos poner en `throws` excepciones no controladas, como `RuntimeException`? ¿Debería el método llamador entonces poner `try-catch` en ese caso? ¿Qué sentido tendría?

### Respuesta


## 15. ¿Cuándo se recomienda usar excepciones controladas, como `IOException`, y cuándo no controladas como `IllegalArgumentException`? ¿Existen en todos los lenguajes ambas opciones? En los que sólo existe una opción, ¿cuál es la más habitual?

### Respuesta


## 16. ¿Tiene sentido lanzar excepciones dentro del `catch`? ¿Se puede relanzar la misma excepción capturada? ¿Cuándo tendría sentido hacer esto último? Pon ejemplos de ambos casos.

### Respuesta


## 17. ¿En qué consiste que una excepción sea la **"causa"** de otra excepción? Pon un ejemplo en Java, donde capturemos una excepción de bajo nivel y la encapsulemos en otra personalizada de alto nivel. Cuando una excepción sale por pantalla y tiene una causa, ¿se ve?

### Respuesta

