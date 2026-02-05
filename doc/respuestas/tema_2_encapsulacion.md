<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Encapsulación". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 2. Encapsulación

## 1. En Programación Orientada a Objetos (POO), ¿Qué buscan la **encapsulación** y **la ocultación** de información? Enumera brevemente algunas ventajas de la ocultación de información.

### Respuesta

La encapsulación s busca agrupar dentro de una misma clase tanto los datos como las operaciones que actúan sobre ellos, evitando que otras partes del programa accedan o modifiquen directamente.

La ocultación de información pretende controlar qué detalles internos de una clase quedan visibles desde el exterior y cuáles permanecen privados

La ocultación de información evita dependencias innecesarias entre módulos, también reduce la probabilidad de errores al impedir modificaciones accidentales, favorece la reutilización de componentes, ya que otros desarrolladores pueden utilizarlos sin necesidad de conocer detalles internos y permite asegurar la coherencia del estado de los objetos mediante métodos que controlan los cambios en sus atributos.


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### Respuesta
La interfaz pública de una clase u objeto se entiende como el conjunto de métodos y atributos accesibles desde fuera de la propia clase sin necesidad de exponer cómo están implementadas internamente. 

La ocultación de información permite separar qué se muestra y qué se mantiene oculto. Los detalles internos —atributos privados, estructuras auxiliares, algoritmos— quedan protegidos mediante modificadores como private o protected,

## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### Respuesta
La interfaz pública de una clase debe diseñarse con cuidado porque actúa como el contrato que otros componentes del programa utilizarán para interactuar con ella
Si se diseña sin reflexión, pueden exponerse métodos innecesarios o permitir usos incorrectos del objeto.

Cambiar la interfaz pública no es sencillo, porque cualquier modificación impacta directamente en todo el código que la utiliza. Es recomendable exponer solo lo esencial y mantener la interfaz estable


## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Respuesta

Las invariantes de clase son condiciones que deben cumplirse siempre para que un objeto sea considerado válido durante toda su vida, excepto en momentos puntuales dentro de la ejecución.
Por ejemplo, en una cuenta bancaria, una invariante típica sería que el saldo nunca sea negativo si la clase no permite descubiertos.

La ocultación de información ayuda porque impide el acceso directo e indiscriminado a los atributos internos, lo que evita que código externo rompa accidentalmente estas invariantes


## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### Respuesta
    public class Punto {
    // Atributos ocultos
    private double x;
    private double y;

    // Constructor
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Métodos de acceso (interfaz pública)
    public double getX() {
        return x;
    }

    public double getY() {
        return y;
    }

    // Método de cálculo (interfaz pública)
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
    }

La interfaz pública de la clase Punto está formada por los elementos que cualquier otro código puede invocar desde fuera de la clase. 
En cambio, private restringe el acceso únicamente al interior de la propia clase.


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### Respuesta

En primer lugar, ambos modificadores pueden aplicarse a los atributos y métodos de una clase.

Además, public puede aplicarse a las clases de primer nivel.Sin embargo, private no puede utilizarse en estas; solo es válido para clases internas (clases definidas dentro de otra clase).

Por último, los modificadores también se pueden usar en constructores 


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### Respuesta
En Java existen cuatro niveles de visibilidad: public, private, protected y la visibilidad por defecto (o package‑private).


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### Respuesta


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Respuesta


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### Respuesta


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### Respuesta


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Respuesta


## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### Respuesta


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

### Respuesta


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### Respuesta


## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### Respuesta


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Respuesta


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### Respuesta


## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

### Respuesta


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

### Respuesta


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

### Respuesta


## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### Respuesta


## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado. Añade además cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### Respuesta
