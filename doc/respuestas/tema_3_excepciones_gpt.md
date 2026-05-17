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

En C no existe ningún mecanismo integrado de excepciones, por lo que hay que transmitir el error de otra forma. Una técnica estándar consiste en devolver un valor “sentinela” que indique fallo y dejar el resultado real en un parámetro por referencia. El llamador comprueba ese valor y, en caso negativo, informa al usuario.

```c
double raiz(double x, int *error) {
    if (x < 0.0) {
        *error = 1;
        return 0.0;
    }
    *error = 0;
    return sqrt(x);
}

int main(void) {
    int e;
    double r = raiz(-1.0, &e);
    if (e) {
        printf("Número negativo\n");
    } else {
        printf("Raíz = %f\n", r);
    }
}
```

Otra opción es utilizar variables globales como `errno` o una variable de módulo para almacenar el código de error, y hacer que la función devuelva un valor válido (por ejemplo, -1) cuando se produzca un problema. El llamador debe comprobar `errno` después de invocar `raiz` u otra función.

```c
#include <math.h>
#include <errno.h>

double raiz(double x) {
    if (x < 0.0) {
        errno = EDOM; /* dominio */
        return -1.0;
    }
    errno = 0;
    return sqrt(x);
}

int main(void) {
    double r = raiz(-1.0);
    if (errno == EDOM) {
        printf("Error: argumento negativo\n");
    }
    else {
        printf("Raíz = %f\n", r);
    }
}
```

## 2. Brevemente ¿Qué es una **"excepción"**? ¿Con qué objetivo las usa un programador cuando implementa funciones o cuando las llama?

### Respuesta

Una excepción es un mecanismo del lenguaje para señalar que ha ocurrido una condición inusual o errónea durante la ejecución. A diferencia de un valor de retorno, la excepción “salta” fuera del flujo normal y puede ser tratada por un manejador específico.

Cuando un programador implementa una función, usa excepciones para no tener que propagar manualmente códigos de error; el objetivo es separar la lógica normal de la gestión de fallos. Al llamar a una función, el desarrollador puede capturar la excepción en un bloque `try/catch` y tomar medidas correctoras o informar al usuario.

## 3. Reescribe el mismo ejemplo de raiz, pero en Java, metiendo ese método en una clase `Calculadora` y llama a dicho método desde el método `main`, mostrando cómo se puede controlar desde fuera.

### Respuesta

El método `raiz` se encapsula en una clase y lanza una excepción si el argumento es negativo. El `main` usa un bloque `try` para invocar el método y capturar el fallo.

```java
class Calculadora {
    public static double raiz(double x) {
        if (x < 0) {
            throw new IllegalArgumentException("argumento negativo");
        }
        return Math.sqrt(x);
    }
}

public class Prueba {
    public static void main(String[] args) {
        try {
            double r = Calculadora.raiz(-4.0);
            System.out.println("Resultado: " + r);
        } catch (IllegalArgumentException ex) {
            System.out.println("Error: " + ex.getMessage());
        }
    }
}
```

El control queda “desde fuera” de `raiz`, en el método que la llama; el flujo normal no se mezcla con la comprobación del signo.

## 4. ¿Qué es **"lanzar"** una excepción? ¿Qué es **"controlar"** o **"capturar"** una excepción? ¿Qué es que se **"propague"** una excepción? ¿Qué le va ocurriendo a las funciones en la pila de llamadas por donde se va propagando la excepción? ¿Las funciones que no la controlan se reanudan después de alguna forma? Explica con el mismo ejemplo anterior en Java de la raíz cuadrada.

### Respuesta

**Lanzar** (`throw`) significa crear una instancia de excepción y transferir el control al mecanismo de gestión. **Controlar** o **capturar** (`catch`) consiste en interceptarla en un bloque asociado y ejecutar código de recuperación. **Propagar** es dejar que la excepción salga del método actual sin ser capturada; el runtime busca un manejador más arriba en la pila de llamadas.

Cuando una excepción se propaga, las funciones intermedias se “deshacen” (stack unwinding): sus ejecuciones se terminan, sus variables locales desaparecen y se sale de cada método hasta encontrar un `catch` adecuado. Las funciones que no la controlan no se reanudan jamás; su ejecución queda abortada y no regresan al punto donde se interrumpieron.

Aplicando al ejemplo de `raiz`, si `main` no tiene `try/catch`, la excepción interrumpiría `main`, después el hilo y finalmente el programa entero, mostrando la traza de llamadas.

## 5. ¿Qué ventajas tiene frente a C, la **"propagación natural"** de las excepciones a través de la pila (*stack*) de llamadas?

### Respuesta

La propagación automática ahorra comprobaciones manuales en cada función intermedia; no hay que retornar códigos de error y comprobarlos a cada paso. Permite concentrar la lógica de manejo en un punto adecuado, mejorando la legibilidad y separación de responsabilidades. Además, evita que los detalles de un fallo “contaminen” la firma de muchas funciones, reduciendo el acoplamiento.

## 6. En orientación a objetos, ¿las excepciones suelen ser objetos? ¿Qué ventajas tiene esto en términos de encapsulación? ¿Podemos entonces crear excepciones personalizadas?

### Respuesta

En Java las excepciones son instancias de clases que extienden `Throwable`. Esto significa que pueden llevar datos encapsulados (mensaje, causa, información adicional) y comportamientos propios. La encapsulación facilita ocultar detalles internos del error y exponer sólo lo necesario.

Sí, se pueden crear clases de excepción personalizadas para representar fallos específicos (por ejemplo, `MiExcepcionDeDominio`). Esto permite tipar los manejadores y pasar información extra junto con el objeto.

## 7. En relación con las ventajas de la encapsulación, comparando el ejemplo en C con Java. ¿Qué **información esencial** lleva cualquier **objeto excepción** que es muy útil tener cuando se llega a un manejador?

### Respuesta

Cualquier objeto excepción lleva al menos un *mensaje* descriptivo y una *traza de pila* (stack trace) que indica dónde se lanzó. Esa información es fundamental para diagnosticar el problema desde el manejador: saber qué clase de error ocurrió y en qué localización de código. En C, con el diseño anterior, no existe un contenedor único; el llamador debe inferir el contexto a partir de códigos numéricos, lo cual es menos rico y más propenso a equivocaciones.

## 8. En Java, sobre el bloque **"try-catch"**, ¿se pueden tener más de un bloque `catch`? ¿cuántos bloques `catch` se ejecutan?

### Respuesta

Sí, se puede encadenar más de un `catch` tras un `try`. El runtime evalúa cada `catch` en orden y ejecuta únicamente el primero cuyo tipo es compatible con la exceptión lanzada. Los demás bloques quedan ignorados; no hay doble ejecución ni “caídas” entre ellos.

```java
try { … }
catch (IOException e) { … }
catch (RuntimeException e) { … }
```

Solo se ejecuta un `catch` por excepción.

## 9. Si las excepciones producen rupturas en el código llamador, ¿cómo podemos garantizar que se ejecuta siempre finalmente un código necesario para cierre de ficheros, liberacion de recursos, antes de que continúe propagándose la excepción? Pon un ejemplo en Java con `finally`, tanto con `catch` como sin él.

### Respuesta

El bloque `finally` se utiliza para ejecutar siempre un fragmento de código, con independencia de si se produjo una excepción o no. Esto es útil para cerrar ficheros, liberar recursos, etc.

```java
try {
    fichero.open();
    // operaciones
} catch (IOException ex) {
    System.out.println("Error de E/S");
} finally {
    fichero.close();  // se ejecuta tanto si hubo excepción como si no
}
```

También es válido sin `catch`:

```java
try {
    fichero.open();
    // operaciones
} finally {
    fichero.close();
}
```

La cláusula `finally` garantiza ejecución antes de que la excepción siga propagándose o el método retorne.

## 10. En Java, el bloque `finally` puede ir sin `catch`? ¿Se ejecuta siempre tanto si ocurre como si no ocurre una excepción? ¿Y si hay un `return` en medio del `try`?

### Respuesta

Sí, se puede usar `finally` sin acompañarlo de ningún `catch`; el bloque se ejecuta siempre, ocurra excepción o no. Incluso si dentro del `try` hay un `return`, el contenido de `finally` se ejecuta antes de que el método devuelva el valor. La única forma de evitarlo sería terminar la JVM con `System.exit` u otra situación extrema.

## 11. En Java, qué son las excepciones **"controladas"** y las **"no controladas"**? ¿Qué papel juega `RuntimeException`? Pon un ejemplo de excepciones típicas controladas y no controladas que incluso nosotros mismos podríamos usar. Haz dos listas con 3 o 4 ejemplos de situación donde se suele preferir una excepción controlada y donde se suele preferir una excepción no controlada.

### Respuesta

En Java, las excepciones controladas (checked) son aquellas que no extienden `RuntimeException`; el compilador obliga a declararlas o capturarlas. Se usan para condiciones previsibles y recuperables, como `IOException`, `SQLException` o `ClassNotFoundException`. Las no controladas (unchecked) derivan de `RuntimeException` y representan errores de programación o condiciones irreparables: `NullPointerException`, `IllegalArgumentException`, `ArrayIndexOutOfBoundsException`.

**Ejemplos típicos controlados**  
- Lectura/escribir ficheros (`IOException`)  
- Acceso a base de datos (`SQLException`)  
- Operaciones de reflexión (`ClassNotFoundException`)

**Ejemplos típicos no controlados**  
- Argumento nulo (`NullPointerException`)  
- Índice fuera de límites (`IndexOutOfBoundsException`)  
- Conversión inválida (`NumberFormatException`)

Situaciones donde suelen preferirse :  
1. APIs públicas con errores externos (entradas de usuario, ficheros).  
2. Operaciones I/O o de red.  
3. Interacción con sistemas de terceros.

Situaciones donde se prefieren excepciones no controladas : 
1. Validación interna de parámetros.  
2. Invariantes de clase violadas.  
3. Errores lógicos que el programador debería corregir.

## 12. ¿Qué es y para qué se usa `throws`? ¿Por qué es alternativa a capturar una excepción controlada?

### Respuesta

La cláusula `throws` en la firma de un método declara que éste puede lanzar ciertas excepciones controladas y que no las captura internamente. Es una alternativa a manejarlas allí mismo; obliga al llamador a ocuparse de ellas o volver a declararlas. Permite propagar responsabilidad hacia arriba en la pila.

```java
public void leer() throws IOException { … }
```

## 13. Pon un ejemplo en Java de firma de método que incluya `throws`, de una función que abre un fichero pero que declara que no le interesa menejar la excepción de si el fichero no existe, sino que se propague hacia arriba. Eso sí, acuérdate del `finally`.

### Respuesta

```java
public void abrirFichero(String nombre) throws IOException {
    FileInputStream in = null;
    try {
        in = new FileInputStream(nombre);
        // leer ...
    } finally {
        if (in != null) {
            in.close();
        }
    }
}
```

## 14. ¿Podemos poner en `throws` excepciones no controladas, como `RuntimeException`? ¿Debería el método llamador entonces poner `try-catch` en ese caso? ¿Qué sentido tendría?

### Respuesta

Sí, es legal listar `RuntimeException` en `throws`, pero el compilador no exige que el llamador las capture. No tiene mucho sentido práctico; se usa ocasionalmente como documentación (“este método puede lanzar IllegalStateException”), pero no añade obligación. El llamador puede, si quiere, meter un `try/catch`, pero no está obligado: la propagación continuará si no lo hace.

## 15. ¿Cuándo se recomienda usar excepciones controladas, como `IOException`, y cuándo no controladas como `IllegalArgumentException`? ¿Existen en todos los lenguajes ambas opciones? En los que sólo existe una opción, ¿cuál es la más habitual?

### Respuesta

Se recomienda utilizar excepciones controladas cuando se trata de condiciones externas y recuperables (archivos, red, configuración), de modo que el llamador puede decidir cómo manejarla. Las no controladas se reservan a fallos de programación que deberían detectarse durante el desarrollo. No todos los lenguajes distinguen; por ejemplo, Python y C# sólo tienen excepciones no verificadas. En esos entornos la convención dicta qué excepciones documentar, pero no hay verificación en tiempo de compilación. Java es uno de los pocos con ambas categorías.

## 16. ¿Tiene sentido lanzar excepciones dentro del `catch`? ¿Se puede relanzar la misma excepción capturada? ¿Cuándo tendría sentido hacer esto último? Pon ejemplos de ambos casos.

### Respuesta

Es perfectamente válido lanzar otra excepción dentro de un bloque `catch`, por ejemplo para traducir un error de bajo nivel a uno de dominio:

```java
try {
    procesar();
} catch (IOException ex) {
    throw new MiExcepcion("fallo al procesar", ex);
}
```

También se puede relanzar la misma excepción (`throw ex;` o simplemente `throw;` en otros lenguajes). Tiene sentido cuando se requiere registrar algo o modificar el mensaje, pero se desea que el flujo de propagación continúe:

```java
try {
    leer();
} catch (IOException ex) {
    logger.error("error", ex);
    throw ex;  // sigue propagando
}
```

Relanzar evita silenciar el problema y permite añadir contexto adicional.

## 17. ¿En qué consiste que una excepción sea la **"causa"** de otra excepción? Pon un ejemplo en Java, donde capturemos una excepción de bajo nivel y la encapsulemos en otra personalizada de alto nivel. Cuando una excepción sale por pantalla y tiene una causa, ¿se ve?

### Respuesta

Una excepción puede envolver a otra como su causa, creando una cadena que conserva el origen del error. Esto se hace pasando la excepción inicial al constructor de la nueva.

```java
try {
    abrirConexion();
} catch (SQLException sqlEx) {
    throw new MiErrorAplicacion("no se pudo abrir", sqlEx);
}
```

Al imprimir `MiErrorAplicacion`, la traza generada por `printStackTrace()` incluye automáticamente la causa y su propia traza. Así se ven ambas en la salida estándar, mostrando el error de alto nivel y el motivo original.
