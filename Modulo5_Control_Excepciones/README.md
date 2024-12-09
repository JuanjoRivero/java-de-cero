# **Módulo 5: Manejo de Excepciones**

En este modulo aprenderás a manejar errores de manera controlada y eficaz para mejorar la robustez de los programas, utilizando estructuras específicas para el manejo de excepciones en Java.

---

## **1. ¿Qué es una Excepción?**

Una **excepción** es un evento que interrumpe el flujo normal del programa cuando ocurre un error durante la ejecución.

### **Ejemplos comunes de excepciones:**
- Dividir un número entre cero: `ArithmeticException`.
- Acceder a un índice inválido en un array: `ArrayIndexOutOfBoundsException`.
- Introducir un dato no válido: `NumberFormatException`.

---

## **2. Bloques `try`, `catch` y `finally`**

### **¿Qué hacen estos bloques?**
- **`try`:** Contiene el código que puede generar una excepción.
- **`catch`:** Maneja la excepción si ocurre. Puedes especificar el tipo de excepción a capturar.
- **`finally`:** Código que se ejecuta **siempre**, independientemente de si ocurrió una excepción o no. Se usa para liberar recursos o finalizar tareas.

### **2.1 Estructura básica**
```java
try {
    // Código que puede generar una excepción
} catch (TipoDeExcepcion e) {
    // Código para manejar la excepción
} finally {
    // Código que siempre se ejecuta
}
```

### **2.2 Explicación detallada**

#### **1. Bloque `try`:**
- Contiene el código que queremos ejecutar pero que podría fallar.
- Ejemplo típico: División entre cero.

#### **2. Bloque `catch`:**
- Captura la excepción específica que ocurre.
- Especificamos el tipo de excepción que queremos manejar (como `ArithmeticException`).

#### **3. Bloque `finally`:**
- Se ejecuta siempre, ideal para liberar recursos o imprimir mensajes finales.
- **Ejemplo de uso:** Cerrar archivos o conexiones de red.

### **2.3 Ejemplo práctico: Manejar división por cero**
```java
public class EjemploTryCatch {
    public static void main(String[] args) {
        try {
            int numerador = 10;
            int denominador = 0;
            int resultado = numerador / denominador; // Aquí ocurre una excepción
            System.out.println("Resultado: " + resultado);
        } catch (ArithmeticException e) {
            System.out.println("Error: No se puede dividir entre cero.");
        } finally {
            System.out.println("Cálculo finalizado.");
        }
    }
}
```

#### **Salida:**
```
Error: No se puede dividir entre cero.
Cálculo finalizado.
```

### **2.4 Capturar cualquier excepción con `Exception`**
Además de manejar excepciones específicas, podemos usar `Exception` para capturar cualquier error. Esto es útil cuando queremos asegurarnos de que nuestro programa no falle sin importar qué tipo de excepción ocurra.

#### **Ejemplo:**
```java
public class EjemploException {
    public static void main(String[] args) {
        try {
            int[] numeros = {1, 2, 3};
            System.out.println(numeros[5]); // Genera ArrayIndexOutOfBoundsException
        } catch (Exception e) {
            System.out.println("Error detectado: " + e.getMessage());
        }
    }
}
```

#### **Salida:**
```
Error detectado: Index 5 out of bounds for length 3
```

---

## **3. Comandos útiles en el bloque `catch`**

Cuando se captura una excepción, Java proporciona varios métodos para obtener información sobre el error. Estos comandos son útiles para depuración y para informar al usuario.

| **Comando**                | **Descripción**                                                                       | **Ejemplo**                                         |
|----------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------|
| `e.getMessage()`           | Devuelve un mensaje breve con la causa de la excepción.                               | `"Division by zero"` (para `ArithmeticException`) |
| `e.toString()`             | Devuelve el tipo de excepción y el mensaje asociado.                                  | `"java.lang.ArithmeticException: Division by zero"` |
| `e.printStackTrace()`      | Imprime el seguimiento completo de la pila, mostrando dónde ocurrió la excepción.      | Útil para depuración.                             |
| `e.getCause()`             | Devuelve la causa subyacente de la excepción (si existe).                             | `"null"` si no hay una causa específica.          |

### **Ejemplo práctico con comandos útiles**
```java
public class EjemploComandosCatch {
    public static void main(String[] args) {
        try {
            int[] numeros = {1, 2, 3};
            System.out.println(numeros[5]); // Error
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Mensaje: " + e.getMessage());
            System.out.println("Tipo y mensaje: " + e.toString());
            System.out.print("Traza completa: ");
            e.printStackTrace(); // Depuración
        }
    }
}
```

#### **Salida:**
```
Mensaje: Index 5 out of bounds for length 3
Tipo y mensaje: java.lang.ArrayIndexOutOfBoundsException: Index 5 out of bounds for length 3
Traza completa: 
java.lang.ArrayIndexOutOfBoundsException: Index 5 out of bounds for length 3
	at EjemploComandosCatch.main(EjemploComandosCatch.java:5)
```

---

## **4. Lanzar excepciones con `throw`**

### **¿Qué es `throw`?**
El bloque `throw` se utiliza para **lanzar** una excepción de forma manual, permitiendo que el programa detecte errores de forma controlada.

### **4.1 Ejemplo básico: Lanzar una excepción**
```java
public class EjemploThrow {
    public static void validarEdad(int edad) {
        if (edad < 0) {
            throw new IllegalArgumentException("La edad no puede ser negativa.");
        }
        System.out.println("Edad válida: " + edad);
    }

    public static void main(String[] args) {
        try {
            validarEdad(-5); // Esto lanza una excepción
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

#### **Salida:**
```
Error: La edad no puede ser negativa.
```

---

## **5. Propagar excepciones con `throws`**

### **¿Qué es `throws`?**
Cuando un método puede generar una excepción, usamos `throws` para indicarlo en su definición. Esto permite que otros métodos o el programa principal manejen esa excepción.

### **5.1 Ejemplo práctico: Propagar excepciones**
En lugar de usar `BufferedReader`, utilizaremos un ejemplo más sencillo: conversión de texto a número.

```java
public class EjemploThrows {
    // Este método lanza una excepción si no se ingresa un número válido
    public static int convertirTextoANumero(String texto) throws NumberFormatException {
        return Integer.parseInt(texto);
    }

    public static void main(String[] args) {
        try {
            int numero = convertirTextoANumero("abc"); // Esto lanza una excepción
            System.out.println("Número convertido: " + numero);
        } catch (NumberFormatException e) {
            System.out.println("Error: No ingresaste un número válido.");
        }
    }
}
```

#### **Salida:**
```
Error: No ingresaste un número válido.
```

---

## **6. Ejercicios Prácticos**

### **Nivel Básico**
1. **Validación de entrada:**
   - Escribe un programa que solicite un número al usuario y maneje la excepción `NumberFormatException` si el usuario introduce texto.

2. **División segura:**
   - Solicita dos números al usuario y realiza la división. Si el denominador es cero, maneja la excepción y pide un número válido.

3. **Cerrar recursos:**
   - Simula la lectura de un archivo (sin necesidad de usar uno real). Asegúrate de imprimir un mensaje en el bloque `finally`.

### **Nivel Intermedio**
1. **Validación de rango:**
   - Solicita un número entre 1 y 100. Si el número está fuera de rango, lanza una excepción personalizada `RangoInvalidoException`.

2. **Propagar excepciones:**
   - Crea un método que convierta una cadena a número entero y declare `throws NumberFormatException`. Maneja la excepción en el programa principal.

### **Nivel Avanzado**
1. **Gestión de múltiples errores:**
   - Diseña un programa que:
     - Valide la entrada del usuario.
     - Lea un archivo inexistente (puedes simularlo con un mensaje).
     - Lance una excepción personalizada si los datos no cumplen con un criterio específico.

2. **Sistema bancario:**
   - Crea un programa con excepciones personalizadas para manejar errores como:
     - Retiro mayor al saldo disponible.
     - Montos negativos en las operaciones.