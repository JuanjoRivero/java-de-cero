

# **Módulo 6: Testing con JUnit**

En este módulo vas a aprender a escribir, ejecutar y gestionar pruebas unitarias utilizando JUnit, con el fin de asegurar que el código funcione correctamente y de manera predecible.

---

## **1. Introducción a JUnit**

JUnit es un framework para realizar pruebas unitarias en Java. Las pruebas unitarias verifican que **una pequeña parte del código (como una función o método)** se comporte según lo esperado de manera aislada. Esto asegura que los componentes del sistema funcionen correctamente antes de integrarlos con otros.

### **1.1 ¿Por qué usar JUnit?**

#### **Beneficios principales:**
- Automatiza la ejecución de pruebas.
- Detecta errores rápidamente durante el desarrollo.
- Mejora la calidad del código y su mantenimiento.
- Es esencial en metodologías ágiles y procesos de desarrollo continuo.

### **1.2 Configuración de JUnit en un proyecto Maven**

#### **Paso 1: Añadir la dependencia de JUnit en `pom.xml`**

JUnit debe estar configurado como dependencia para ser usado en tu proyecto. Si estás usando **JUnit 5**, incluye lo siguiente en el archivo `pom.xml`:

```xml
<dependencies>
    <!-- JUnit 5 API -->
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>5.9.3</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

#### **Paso 2: Crear el directorio de pruebas**

1. Maven crea un proyecto con la siguiente estructura básica:
   ```
   src/
   ├── main/
   │   └── java/       # Código principal
   └── test/
       └── java/       # Código de pruebas
   ```

2. Asegúrate de colocar tus clases de prueba en el directorio `src/test/java`.

### **1.3 Estructura básica de una prueba unitaria**

#### **Pasos básicos:**
1. **Preparar el entorno:** Configura los datos iniciales o el objeto a probar.
2. **Ejecutar el método:** Llama al método que deseas probar.
3. **Verificar el resultado:** Usa aserciones para comparar los resultados esperados y reales.

#### **Ejemplo básico:**
```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

public class CalculadoraTest {
    @Test
    public void testSuma() {
        int resultado = Calculadora.sumar(2, 3);
        assertEquals(5, resultado);  // Verifica que 2 + 3 sea igual a 5
    }
}
```

#### **Salida esperada:**
```
Prueba pasada si el resultado es 5.
```

---

## **2. Métodos y anotaciones de JUnit**

### **2.1 Métodos de aserción**

| **Método**                 | **Descripción**                                                         | **Ejemplo**                                  |
|----------------------------|-------------------------------------------------------------------------|----------------------------------------------|
| `assertEquals(expected, actual)` | Verifica que los valores esperado y actual sean iguales.                  | `assertEquals(5, suma(2, 3));`               |
| `assertTrue(condition)`    | Verifica que la condición sea verdadera.                                | `assertTrue(esPositivo(5));`                 |
| `assertFalse(condition)`   | Verifica que la condición sea falsa.                                    | `assertFalse(esNegativo(10));`               |
| `assertNull(object)`       | Verifica que el objeto sea `null`.                                      | `assertNull(miObjeto);`                      |
| `assertNotNull(object)`    | Verifica que el objeto no sea `null`.                                   | `assertNotNull(lista);`                      |
| `assertThrows(exception, executable)` | Verifica que se lance una excepción específica.                     | `assertThrows(ArithmeticException.class, () -> dividir(5, 0));` |


### **2.2 Anotaciones de JUnit**

| **Anotación**       | **Descripción**                                                                                   |
|---------------------|---------------------------------------------------------------------------------------------------|
| `@Test`            | Marca un método como una prueba unitaria.                                                         |
| `@BeforeEach`      | Método que se ejecuta **antes de cada prueba** para inicializar configuraciones.                   |
| `@AfterEach`       | Método que se ejecuta **después de cada prueba** para limpiar recursos.                            |
| `@BeforeAll`       | Método que se ejecuta una vez **antes de todas las pruebas** en una clase. Debe ser `static`.      |
| `@AfterAll`        | Método que se ejecuta una vez **después de todas las pruebas** en una clase. Debe ser `static`.    |
| `@Disabled`        | Marca una prueba como deshabilitada, es decir, no se ejecutará.                                    |

#### **Ejemplo:**
```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

public class CalculadoraTest {
    private Calculadora calculadora;

    @BeforeEach
    public void setup() {
        calculadora = new Calculadora(); // Configuración antes de cada prueba
    }

    @Test
    public void testSuma() {
        assertEquals(5, calculadora.sumar(2, 3));
    }

    @Test
    public void testMultiplicacion() {
        assertEquals(20, calculadora.multiplicar(4, 5));
    }
}
```

---

## **3. Ejercicios Prácticos**

Vamos a practicarlo basandonos en este código:

### **Código Base: Calculadora Avanzada**

```java
public class Calculadora {
    // Suma de dos números
    public static int sumar(int a, int b) {
        return a + b;
    }

    // Resta de dos números
    public static int restar(int a, int b) {
        return a - b;
    }

    // Multiplicación de dos números
    public static int multiplicar(int a, int b) {
        return a * b;
    }

    // División de dos números (maneja división por cero)
    public static double dividir(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("No se puede dividir por cero.");
        }
        return (double) a / b;
    }

    // Calcula el área de un círculo
    public static double areaCirculo(double radio) {
        if (radio < 0) {
            throw new IllegalArgumentException("El radio no puede ser negativo.");
        }
        return Math.PI * radio * radio;
    }

    // Verifica si un número es par
    public static boolean esPar(int numero) {
        return numero % 2 == 0;
    }
}
```

---

### **Ejercicios de Creación de Tests**

#### **Nivel Básico**

1. **Prueba para el método `sumar`:**
   - Crea una prueba unitaria que verifique si la suma de dos números es correcta.
   - Asegúrate de probar al menos dos casos diferentes, como números positivos y negativos.

2. **Prueba para el método `restar`:**
   - Verifica que la resta funcione correctamente.
   - Incluye pruebas donde el resultado sea cero, positivo y negativo.

3. **Prueba para el método `esPar`:**
   - Escribe pruebas unitarias para verificar si el método identifica correctamente números pares e impares.

#### **Nivel Intermedio**

1. **Prueba para el método `multiplicar`:**
   - Verifica que el método funcione correctamente con:
     - Números positivos.
     - Números negativos.
     - Uno de los números siendo cero.

2. **Prueba para el método `dividir`:**
   - Crea pruebas para:
     - Dividir números positivos.
     - Dividir un número negativo por uno positivo.
     - Lanzar una excepción cuando el divisor sea cero usando `assertThrows`.

3. **Prueba para el método `areaCirculo`:**
   - Verifica que el área se calcule correctamente para diferentes radios.
   - Asegúrate de que el método lance una excepción si el radio es negativo.

#### **Nivel Avanzado**

1. **Prueba combinada de cálculos:**
   - Diseña un test que combine los métodos de la calculadora en una operación más compleja, por ejemplo:
     - Multiplicar dos números y luego dividir el resultado por un tercero.
   - Verifica que el resultado final sea correcto.

2. **Prueba de múltiples excepciones:**
   - Escribe pruebas que verifiquen las excepciones en:
     - `dividir`, si el divisor es cero.
     - `areaCirculo`, si el radio es negativo.

3. **Pruebas de límite:**
   - Verifica que los métodos manejen correctamente los límites máximos y mínimos de los números enteros (`Integer.MAX_VALUE` y `Integer.MIN_VALUE`).
