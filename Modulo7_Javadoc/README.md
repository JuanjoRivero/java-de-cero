

# **Módulo 7: Documentación con Javadoc**

En este módulo vas a aprender a documentar correctamente el código en Java utilizando Javadoc para generar una documentación profesional y legible, facilitando la comprensión y el mantenimiento del software.

---

## **1. ¿Qué es Javadoc?**

**Javadoc** es una herramienta incluida en el JDK de Java que permite generar documentación en formato HTML a partir de comentarios especiales en el código fuente.

### **Beneficios de usar Javadoc:**
- Proporciona una documentación detallada y estructurada directamente desde el código.
- Facilita la colaboración en equipos de desarrollo.
- Sirve como referencia para otros desarrolladores que usen nuestras clases y métodos.

---

## **2. Cómo escribir comentarios Javadoc**

Los comentarios Javadoc están delimitados por `/**` y `*/`. 

### **Ejemplo básico:**
```java
/**
 * Esta clase representa una calculadora básica con operaciones aritméticas.
 */
public class Calculadora {
    /**
     * Suma dos números enteros.
     *
     * @param a El primer número.
     * @param b El segundo número.
     * @return La suma de los dos números.
     */
    public static int sumar(int a, int b) {
        return a + b;
    }
}
```

---

## **3. Estructura de un comentario Javadoc**

Un comentario Javadoc debe incluir:
1. **Descripción breve:** Indica qué hace la clase, método o atributo.
2. **Etiquetas específicas:** Añaden detalles como parámetros, valores de retorno, excepciones, etc.

### **Etiquetas comunes:**

| **Etiqueta**         | **Descripción**                                                                 |
|-----------------------|---------------------------------------------------------------------------------|
| `@param`             | Describe un parámetro del método.                                               |
| `@return`            | Explica lo que devuelve el método.                                              |
| `@throws` o `@exception` | Describe las excepciones que el método puede lanzar.                            |
| `@author`            | Indica el autor del código.                                                    |
| `@version`           | Especifica la versión de la clase o del método.                                 |
| `@see`               | Referencia a otras clases, métodos o documentación relacionada.                 |
| `@deprecated`        | Marca un elemento como obsoleto y no recomendado para su uso.                  |
| `@since`             | Indica desde qué versión está disponible un elemento.                          |
| `@serial`            | Documenta campos serializables.                                                |

---

## **4. Ejemplos prácticos**

### **4.1 Documentar una clase**
```java
/**
 * Clase que proporciona operaciones matemáticas básicas.
 *
 * @author John Doe
 * @version 1.0
 * @since 2023
 */
public class Calculadora {
    // Métodos aquí
}
```


### **4.2 Documentar un método**
```java
/**
 * Calcula el área de un círculo.
 *
 * @param radio El radio del círculo. Debe ser mayor o igual a 0.
 * @return El área del círculo.
 * @throws IllegalArgumentException Si el radio es negativo.
 */
public static double calcularAreaCirculo(double radio) {
    if (radio < 0) {
        throw new IllegalArgumentException("El radio no puede ser negativo.");
    }
    return Math.PI * radio * radio;
}
```


### **4.3 Documentar un atributo**
```java
/**
 * Indica el valor de PI usado para cálculos matemáticos.
 */
public static final double PI = 3.14159;
```


### **4.4 Documentar una excepción**
```java
/**
 * Divide dos números.
 *
 * @param numerador El número a dividir.
 * @param denominador El número por el que se divide. No puede ser 0.
 * @return El resultado de la división.
 * @throws ArithmeticException Si el denominador es 0.
 */
public static double dividir(int numerador, int denominador) {
    if (denominador == 0) {
        throw new ArithmeticException("No se puede dividir por cero.");
    }
    return (double) numerador / denominador;
}
```

---

## **5. Generar la documentación HTML**

### **5.1 Generar Javadoc desde la terminal**
1. Abre la terminal o consola.
2. Navega al directorio donde se encuentra tu código fuente.
3. Usa el siguiente comando para generar la documentación:
   ```bash
   javadoc -d docs -sourcepath src -subpackages tu.paquete
   ```
   - `-d docs`: Especifica el directorio donde se generará la documentación.
   - `-sourcepath src`: Indica el directorio donde está el código fuente.
   - `-subpackages tu.paquete`: Genera documentación para todos los subpaquetes.

### **5.2 Generar Javadoc desde IntelliJ IDEA**
1. Ve al menú **Tools** y selecciona **Generate Javadoc**.
2. Configura las opciones necesarias, como el directorio de salida.
3. Haz clic en **OK** para generar la documentación.

---

## **6. Ejercicios Prácticos**

### **Ejercicio 1: Documentar una clase simple**
Dado el siguiente código, agrega comentarios Javadoc para documentar la clase y los métodos:

```java
public class Conversor {
    public static double celsiusAFahrenheit(double celsius) {
        return celsius * 9/5 + 32;
    }

    public static double fahrenheitACelsius(double fahrenheit) {
        return (fahrenheit - 32) * 5/9;
    }
}
```

### **Ejercicio 2: Documentar excepciones**
Agrega comentarios Javadoc para este código, especificando las excepciones que lanza el método:

```java
public class Divisor {
    public static double dividir(int numerador, int denominador) {
        if (denominador == 0) {
            throw new ArithmeticException("No se puede dividir por cero.");
        }
        return (double) numerador / denominador;
    }
}
```

### **Ejercicio 3: Completar la documentación de un proyecto**
Dado el siguiente fragmento de código de una calculadora, documenta completamente las clases, atributos y métodos, incluyendo etiquetas como `@since`, `@version` y `@deprecated`:

```java
public class CalculadoraAvanzada {
    public double potencia(double base, double exponente) {
        return Math.pow(base, exponente);
    }

    /**
     * @deprecated Este método será eliminado en la próxima versión.
     */
    public double raizCuadrada(double numero) {
        return Math.sqrt(numero);
    }
}
```