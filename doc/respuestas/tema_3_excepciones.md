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

En C, donde no hay manejo de excepciones incorporado, se suelen utilizar valores de retorno especiales o punteros para indicar errores. En el caso de una función que calcula la raíz cuadrada de un número flotante positivo, podrías diseñar la función de la siguiente manera para controlar el error si se le pasa un número negativo. Aquí hay dos opciones diferentes:
###### Opción 1: Utilizando un puntero para el resultado y un valor de retorno para el estado
```C++
#include 
int calcularRaizCuadrada(float numero, float *resultado) { 
	if (numero < 0) { 
// Informar del error 
		printf("Error: No se puede calcular la raíz cuadrada de un número negativo.\n"); 
		return -1;
// Valor de retorno que indica un error 
	} 
	*resultado = sqrt(numero); return 0;
// Éxito
} 
int main() { 
	float numero = -5.0; float resultado; 
	int estado = calcularRaizCuadrada(numero, &resultado);
	if (estado == 0) { 
		printf("La raíz cuadrada de %.2f es %.2f\n", numero, resultado); 
	} 
	return 0;
}
```
###### Opción 2: Utilizando un valor especial para indicar error
```c++
#include 
#define ERROR_RAIZ_NEGATIVA -1 
float calcularRaizCuadrada(float numero) { 
	if (numero < 0) { 
// Informar del error 
		printf("Error: No se puede calcular la raíz cuadrada de un número negativo.\n"); 
		return ERROR_RAIZ_NEGATIVA; 
// Valor especial que indica un error 
	} 
	return sqrt(numero);
} 
int main() { 
	float numero = -5.0; 
	float resultado = calcularRaizCuadrada(numero);
	if (resultado != ERROR_RAIZ_NEGATIVA) { 
		printf("La raíz cuadrada de %.2f es %.2f\n", numero, resultado); 
		}
	return 0; 
}
```
En ambos casos, la función devuelve un valor especial o utiliza un puntero para el resultado junto con un valor de retorno para indicar si se produjo un error. Esto permite al usuario de la función tomar decisiones basadas en el estado de la operación y manejar adecuadamente los errores.

**a. Devolver "valores especiales"
```java
float raiz(float numero){
	if (numero < 0){
		// situacion "excepcional"
		return -1;
	}
	else{
		return sqrt(numero);
	}
}
main(){
	float resultado = raiz (numero_leido_teclado);
	if (resultado < 0){
		// no hay raiz	
	}
	else{
		//si la hay 
	}
}
```
b. Tener parámetros adicionales para establecer un error
```java
float raiz (float num, int* codigoerror){
	if (num < 0){
		*codigoerror = 1;
		return 0;
	}
	else{
		*codigoerror = 0;
		return sqrt (num);
	}
}
main(){
	int codigoerror= 0 ;
	float resultado = raiz (numero_leido_teclado, &codigoerror);
	if (codigoerror != 0){
		// no hay raiz	
	}
	else{
		//si la hay 
	}
}
```

## 2. Brevemente ¿Qué es una **"excepción"**? ¿Con qué objetivo las usa un programador cuando implementa funciones o cuando las llama?

Una excepción es un evento inusual o imprevisto que interrumpe el flujo normal de ejecución de un programa. Los programadores las utilizan para manejar situaciones de error o condiciones excepcionales de forma estructurada. Al implementar funciones o llamarlas, se pueden utilizar excepciones para señalar y gestionar situaciones anómalas, proporcionando una manera más clara y específica de manejar errores. Esto permite separar el código de manejo de errores del código principal, lo que mejora la legibilidad y mantenibilidad del programa al centralizar el manejo de errores en lugar de dispersarlo por todo el código.

## 3. Reescribe el mismo ejemplo de raiz, pero en Java, metiendo ese método en una clase `Calculadora` y llama a dicho método desde el método `main`, mostrando cómo se puede controlar desde fuera.

La raíz cuadrada en Java, encapsulado en una clase `Calculadora` y llamando al método desde el método `main`:
```java
public class Calculadora { 
	public static double calcularRaizCuadrada(double numero) throws IllegalArgumentException { 
		if (numero < 0) { 
			// Lanzar una excepción para indicar el error 
			throw new IllegalArgumentException("No se puede calcular la raíz cuadrada de un número negativo."); 
		} return Math.sqrt(numero);
	}
	 public static void main(String[] args) { 
		double numero = -5.0; 
		try { 
			double resultado = calcularRaizCuadrada(numero); 
			System.out.println("La raíz cuadrada de " + numero + " es " + resultado);
		} catch (IllegalArgumentException e) { 
			// Capturar la excepción y mostrar el mensaje de error 
			System.out.println("Error: " + e.getMessage());
		}
	}
}
```
La clase `Calculadora` tiene un método estático `calcularRaizCuadrada` que lanza una excepción `IllegalArgumentException` si se recibe un número negativo. En el método `main`, se llama a este método dentro de un bloque `try-catch` para capturar y manejar la excepción en caso de que ocurra, mostrando un mensaje de error. Este enfoque permite un control más estructurado de errores y facilita el manejo de condiciones excepcionales.

## 4. ¿Qué es **"lanzar"** una excepción? ¿Qué es **"controlar"** o **"capturar"** una excepción? ¿Qué es que se **"propague"** una excepción? ¿Qué le va ocurriendo a las funciones en la pila de llamadas por donde se va propagando la excepción? ¿Las funciones que no la controlan se reanudan después de alguna forma? Explica con el mismo ejemplo anterior en Java de la raíz cuadrada.

En Java, al trabajar con excepciones como la raíz cuadrada, es crucial comprender cómo lanzar, controlar y propagar excepciones.  
1. Lanzar una excepción implica notificar un problema durante la ejecución de un método utilizando `throw`, como cuando `calcularRaizCuadrada` recibe un número negativo.  
2. Controlar una excepción implica manejarla con un bloque `try-catch`, como en el método `main` al llamar a `calcularRaizCuadrada`.  
3. La propagación de una excepción permite pasarla a métodos superiores sin manejarla, hasta encontrar un bloque `try-catch` adecuado, evitando la reanudación de funciones no controladas.  
4. Las funciones en la pila de llamadas son examinadas en busca de manejo de excepciones. Si no se encuentra, la ejecución regresa a la función anterior, pudiendo terminar abruptamente si no se maneja adecuadamente. Es esencial gestionar excepciones para una ejecución controlada y prevenir fallos inesperados en el programa en Java.
## 5. ¿Qué ventajas tiene frente a C, la **"propagación natural"** de las excepciones a través de la pila (*stack*) de llamadas?

La propagación de excepciones a través de la pila de llamadas en lenguajes como Java simplifica el manejo de errores en comparación con el enfoque manual en C. Conduce a un código más limpio y legible al separar la lógica de manejo de errores del flujo principal del programa. Además, reduce la complejidad al eliminar la necesidad de verificar manualmente los valores de retorno para detectar errores. Esto mejora el diseño de API al permitir a los diseñadores enfocarse en la funcionalidad principal. La flexibilidad de la propagación de excepciones permite manejar errores de manera más robusta y adaptable. En resumen, la propagación natural de excepciones en lenguajes como Java ofrece ventajas significativas en términos de simplificación, reducción de complejidad, mejora en el diseño de API y mayor flexibilidad en el manejo de errores.

## 6. En orientación a objetos, ¿las excepciones suelen ser objetos? ¿Qué ventajas tiene esto en términos de encapsulación? ¿Podemos entonces crear excepciones personalizadas?

Sí, en programación orientada a objetos, las excepciones suelen ser representadas como objetos en lenguajes como Java y Python. En Java, por ejemplo, todas las excepciones son subclases de la clase `java.lang.Exception`. Esto permite encapsular información sobre el error, crear excepciones personalizadas y manejar errores de manera flexible. Para crear una excepción personalizada, simplemente se define una nueva clase que herede de la clase base de excepción adecuada y se pueden añadir campos y métodos según sea necesario. En resumen, representar las excepciones como objetos en programación orientada a objetos brinda ventajas como encapsulación, extensibilidad y flexibilidad en el manejo de errores.

## 7. En relación con las ventajas de la encapsulación, comparando el ejemplo en C con Java. ¿Qué **información esencial** lleva cualquier **objeto excepción** que es muy útil tener cuando se llega a un manejador?

La encapsulación de la información en objetos excepción en Java facilita el manejo y comunicación de errores en comparación con C. Los objetos excepción en Java contienen información esencial, como un mensaje descriptivo del error, el contexto de la excepción (como el método y la línea de código), datos relevantes (como valores de variables) y un stack trace. Esto ayuda a informar al usuario, registrar el error en los registros de la aplicación, depurar y resolver el problema de manera eficiente. La inclusión de esta información en los objetos excepción en Java proporciona una ventaja significativa en el manejo de excepciones en comparación con otros lenguajes como C.     


## 8. En Java, sobre el bloque **"try-catch"**, ¿se pueden tener más de un bloque `catch`? ¿Cuántos bloques `catch` se ejecutan?

Sí, en Java es posible tener más de un bloque `catch` asociado a un bloque `try`. Esto se utiliza para manejar diferentes tipos de excepciones de manera específica. La estructura básica es la siguiente:
```java
try { 
	// Código que podría lanzar excepciones 
} catch (TipoDeExcepcion1 e1) { 
	// Manejo específico para TipoDeExcepcion1 
} catch (TipoDeExcepcion2 e2) { 
	// Manejo específico para TipoDeExcepcion2 
} catch (OtroTipoDeExcepcion e3) { 
	// Manejo específico para OtroTipoDeExcepcion 
} finally { 
	// Código que se ejecuta siempre, ocurra o no una excepción
}
```
El bloque `try` lanza excepciones que son capturadas por bloques `catch` en orden. Si no ocurre ninguna excepción, se omiten. Un bloque `finally` se ejecuta siempre.

## 9. Si las excepciones producen rupturas en el código llamador, ¿cómo podemos garantizar que se ejecuta siempre finalmente un código necesario para cierre de ficheros, liberacion de recursos, antes de que continúe propagándose la excepción? Pon un ejemplo en Java con `finally`, tanto con `catch` como sin él.

En Java, el bloque `finally` se utiliza para asegurar que cierto código se ejecute, independientemente de si se produjo una excepción o no dentro del bloque `try`. Esto es especialmente útil para tareas como cierre de archivos, liberación de recursos o limpieza de conexiones a bases de datos. Aquí tienes un ejemplo tanto con `catch` como sin él:
###### Con `catch`:
```java
import java.io.BufferedReader; 
import java.io.FileReader; 
import java.io.IOException; 
public class FinallyExampleWithCatch { 
	public static void main(String[] args) { 
		BufferedReader reader = null; 
		try { 
			reader = new BufferedReader(new FileReader("archivo.txt")); 
			String linea; 
			while ((linea = reader.readLine()) != null) {
				System.out.println(linea); 
			}
		} catch (IOException e) { 
			System.out.println("Error al leer el archivo: " + e.getMessage()); 
		} finally {
			try {
				if (reader != null) { 
					reader.close(); 
				}
			} catch (IOException e) { 
				System.out.println("Error al cerrar el archivo: " + e.getMessage());
			}
		}
	}
}
```
En este ejemplo, el bloque `finally` se utiliza para asegurarse de que el archivo se cierre correctamente, incluso si se produce una excepción durante la lectura del archivo.
###### Sin `catch`:
```java
import java.io.BufferedReader; 
import java.io.FileReader; 
import java.io.IOException; 
public class FinallyExampleWithoutCatch { 
	public static void main(String[] args) {
		BufferedReader reader = null; 
			try { 
				reader = new BufferedReader(new FileReader("archivo.txt")); 
				String linea;
				while ((linea = reader.readLine()) != null) {
					System.out.println(linea); 
				}
			} finally {
				try { 
					if (reader != null) { 
						reader.close(); 
					}
				}
				catch (IOException e) { 
					System.out.println("Error al cerrar el archivo: " + e.getMessage()); 
				}
			}
		}
	}
```
En este segundo ejemplo, no hay un bloque `catch`, por lo que cualquier excepción que ocurra durante la lectura del archivo se propagará al método `main`. Sin embargo, el bloque `finally` aún se ejecutará para garantizar que el archivo se cierre correctamente antes de que la excepción continúe propagándose.

En ambos casos, el bloque `finally` garantiza que se ejecute código importante de limpieza o liberación de recursos antes de que la excepción continúe propagándose o antes de que el flujo del programa continúe.

## 10. En Java, el bloque `finally` puede ir sin `catch`? ¿Se ejecuta siempre tanto si ocurre como si no ocurre una excepción? ¿Y si hay un `return` en medio del `try`?

Sí, en Java, el bloque `finally` puede ir sin `catch`. El bloque `finally` se utiliza para contener código que se ejecutará siempre, independientemente de si se produce una excepción o no en el bloque `try`. Su formato básico es:
```java
try { 
// Código que puede lanzar excepciones 
} 
finally { 
// Código que se ejecutará siempre, ocurra o no una excepción 
}
```
El bloque `finally` se ejecuta siempre, tanto si ocurre una excepción como si no. Esto lo hace útil para tareas como la liberación de recursos, cierre de archivos o conexiones a bases de datos, que deben realizarse independientemente del flujo normal del programa.

En cuanto a la pregunta sobre un `return` en medio del bloque `try`, el bloque `finally` se ejecutará incluso si hay un `return` dentro del `try`. El bloque `finally` se ejecuta antes de que el control de flujo salga del método, permitiendo así realizar acciones de limpieza o liberación de recursos antes de que se produzca la salida del método.


## 11. En Java, qué son las excepciones **"controladas"** y las **"no controladas"**? ¿Qué papel juega `RuntimeException`? Pon un ejemplo de excepciones típicas controladas y no controladas que incluso nosotros mismos podríamos usar. Haz dos listas con 3 o 4 ejemplos de situación donde se suele preferir una excepción controlada y donde se suele preferir una excepción no controlada.

En Java, las excepciones se clasifican en dos categorías: controladas y no controladas.
- Las **excepciones controladas** deben ser tratadas explícitamente mediante bloques `try-catch` o declaradas en la firma del método con `throws`. Ejemplos incluyen `IOException` y `SQLExc` `ption`.
- Las **excepciones no controladas** no requieren manejo explícito. Estas son subclases de `RuntimeException` o de `Error`, como `NullPointerException` y `IllegalArgumentException`.
La subclase `RuntimeException` se refiere a excepciones que pueden surgir durante la ejecución sin necesidad de ser manejadas. La palabra clave `throws` en la firma del método indica que el método puede lanzar excepciones específicas, trasladando la responsabilidad del manejo de la excepción al método que invoca al que la lanza, en lugar de gestionarlo dentro del mismo método.


## 12. ¿Qué es y para qué se usa `throws`? ¿Por qué es alternativa a capturar una excepción controlada?

`throws` es una palabra clave en Java que se utiliza en la firma de un método para indicar que ese método **puede lanzar** ciertos tipos de excepciones durante su ejecución, y que no las va a manejar internamente. se usa para **declarar excepciones que un método puede lanzar**: Advierte a quien llame al método que debe estar preparado para manejar esas excepciones. **Propagar excepciones**: Permite que la excepción "ascienda" por la pila de llamadas hasta encontrar un manejador apropiado. **Cumplir con la regla "handle-or-declare"**: Para excepciones controladas (checked exceptions), debes elegir entre capturarlas (try-catch) o declararlas con `throws`.
Con excepciones controladas tienes 2 opciones:
```java
// Opción 1: CAPTURAR (try-catch)
public void metodo1() {
    try {
        // código con posible excepción
    } catch (IOException e) {
        // manejo aquí
    }
}
// Opción 2: DECLARAR (throws)  
public void metodo2() throws IOException {
    // código con posible excepción
    // NO se maneja, se pasa al llamador
}
```
**Usas `throws` cuando** el método actual **no puede manejar** adecuadamente el error y prefieres que lo maneje quien te llamó.

## 13. Pon un ejemplo en Java de firma de método que incluya `throws`, de una función que abre un fichero pero que declara que no le interesa manejar la excepción de si el fichero no existe, sino que se propague hacia arriba. Eso sí, acuérdate del `finally`.

un ejemplo en Java de la firma de un método que utiliza la palabra clave `throws` para indicar que puede lanzar una excepción, pero que no maneja explícitamente la excepción en sí, y utiliza un bloque `finally` para garantizar la liberación de recursos:
```java
import java.io.BufferedReader; 
import java.io.FileReader; 
import java.io.IOException; 
public class FileHandler { 
	public static void main(String[] args) { 
		try { 
			leerArchivo("archivo.txt");
		} catch (IOException e) { 
			System.out.println("Error al leer el archivo: " + e.getMessage()); 
		} 
	} 
	public static void leerArchivo(String nombreArchivo) throws IOException { 
		BufferedReader reader = null; 
		try { 
			reader = new BufferedReader(new FileReader(nombreArchivo)); 
			String linea; 
			while ((linea = reader.readLine()) != null) { 
				System.out.println(linea); 
			} 
		} 
		finally {
// Cerrar el archivo en el bloque finally para asegurar que se cierre siempre
			if (reader != null) { 
				try { 
					reader.close(); 
				} catch (IOException e) {
					System.out.println("Error al cerrar el archivo: " + e.getMessage()); 
				} 
			} 
		} 
	} 
}
```


En este ejemplo, el método `leerArchivo()` declara que puede lanzar una excepción de tipo `IOException` utilizando la palabra clave `throws`. Sin embargo, no maneja explícitamente la excepción dentro del método; en su lugar, la excepción se propaga hacia arriba para que sea manejada por el método que llamó a `leerArchivo()`.

El bloque `finally` se utiliza para garantizar que el archivo se cierre correctamente, independientemente de si se produce una excepción durante la lectura del archivo o no. Esto asegura una liberación adecuada de los recursos utilizados y ayuda a evitar posibles pérdidas de memoria o bloqueos de recursos.
  


## 14. ¿Podemos poner en `throws` excepciones no controladas, como `RuntimeException`? ¿Debería el método llamador entonces poner `try-catch` en ese caso? ¿Qué sentido tendría?

Sí, se puede incluir excepciones no controladas como `RuntimeException` en la cláusula `throws` de un método en Java, aunque no es habitual ni aconsejable, ya que estas excepciones no requieren manejo explícito. Cuando un método declara que puede lanzar una excepción no controlada, el método llamador no está obligado a capturarla, dado que no se espera que ocurra durante la ejecución normal. Usar un bloque `try-catch` para manejar una `RuntimeException` generalmente carece de sentido, a menos que haya un motivo específico para hacerlo, como realizar acciones particulares al ocurrir dicha excepción. Sin embargo, estas situaciones son poco comunes y deben ser abordadas con precaución, dado que las excepciones no controladas suelen señalar errores inesperados en la lógica del programa.

## 15. ¿Cuándo se recomienda usar excepciones controladas, como `IOException`, y cuándo no controladas como `IllegalArgumentException`? ¿Existen en todos los lenguajes ambas opciones? En los que sólo existe una opción, ¿cuál es la más habitual?

Se recomienda usar excepciones controladas y no controladas según el tipo de error y su manejo esperado. 

Las excepciones controladas, como `IOException`, deben emplearse cuando el código puede manejar específicamente el error. Obligan al programador a crear código para gestionar el error, utilizando bloques `try-catch` o propagando la excepción. Se usan en situaciones como operaciones de entrada/salida, manejo de archivos y operaciones de red. 

Por otro lado, las excepciones no controladas, como `IllegalArgumentException`, son adecuadas cuando el error surge de un problema en la lógica del programa o de un estado inesperado. Estas no necesitan ser declaradas ni capturadas por el código que llama al método. Se utilizan para indicar errores imprevistos, que deben corregirse durante el desarrollo y pruebas del software. 

No todos los lenguajes de programación tienen las mismas opciones para manejar excepciones. Por ejemplo, Java permite ambos tipos, mientras que JavaScript maneja principalmente excepciones no controladas, interrumpiendo el flujo si no se gestionan con `try-catch`.


## 16. ¿Tiene sentido lanzar excepciones dentro del `catch`? ¿Se puede relanzar la misma excepción capturada? ¿Cuándo tendría sentido hacer esto último? Pon ejemplos de ambos casos.

Sí.
1. Lanzar una nueva excepción en un `catch`
Se usa para **añadir contexto o transformar el error**.
```java
try {  
    connection.open();  
} catch (SQLException e) {  
    throw new DatabaseException("Error conectando a la BD", e);  
}

```
**Cuándo:** cuando quieres que las capas superiores vean un error **más claro o de tu dominio**.
2. Relanzar la misma excepción
Se captura para **hacer algo (log, limpieza, métricas)** y luego se deja que siga propagándose.
```java
try {  
    processFile();  
} catch (IOException e) {  
    log.error("Error procesando archivo", e);  
    throw e;  
}
```
**Cuándo:** cuando no puedes manejar el error pero necesitas **registrarlo o hacer alguna acción antes**.


## 17. ¿En qué consiste que una excepción sea la **"causa"** de otra excepción? Pon un ejemplo en Java, donde capturemos una excepción de bajo nivel y la encapsulemos en otra personalizada de alto nivel. Cuando una excepción sale por pantalla y tiene una causa, ¿se ve?

En Java, una excepción puede ser la "causa" de otra excepción cuando una excepción original (de bajo nivel) es capturada y encapsulada dentro de una nueva excepción (de alto nivel) para proporcionar más contexto o información sobre el error que ocurrió. La excepción encapsulada se convierte en la causa de la excepción de nivel superior, lo que permite rastrear la cadena de eventos que condujeron al error original.

Aquí tienes un ejemplo en Java que ilustra cómo capturar una excepción de bajo nivel y encapsularla en una nueva excepción personalizada de alto nivel:
```java
public class CustomExceptionExample { 
	public static void main(String[] args) { 
		try { 
			procesarDatos(); 
		} catch (DataProcessingException e) { 
			System.out.println("Se produjo un error al procesar los datos: " +e.getMessage());
			System.out.println("Causa del error: " + e.getCause().getMessage()); 
		} 
	} 
	public static void procesarDatos() throws DataProcessingException { 
		try { 
// Simulando una operación que puede lanzar una excepción de bajo nivel 
			int resultado = 10 / 0; 
// Esto lanzará una excepción ArithmeticException 
		} catch (ArithmeticException e) {
// Capturar la excepción de bajo nivel y encapsularla en una nueva excepción personalizada 
			throw new DataProcessingException("Error al procesar los datos", e); 
			} 
		} 
	} // Excepción personalizada de alto nivel que encapsula una excepción de bajo nivel 
	class DataProcessingException extends Exception { 
		public DataProcessingException(String message, Throwable cause) { 
			super(message, cause);
		} 
	}
}
```


En este ejemplo, el método `procesarDatos()` intenta realizar una operación que puede lanzar una excepción de bajo nivel (`ArithmeticException`) debido a una división por cero. Cuando se captura la excepción de bajo nivel en el bloque `catch`, se encapsula dentro de una nueva excepción personalizada `DataProcessingException` junto con un mensaje descriptivo.

Cuando la excepción de alto nivel es capturada en el método `main()`, se puede acceder a la causa original utilizando el método `getCause()`, lo que permite identificar la causa raíz del error y proporcionar un manejo más detallado y significativo de la excepción.