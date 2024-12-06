# Módulo 1: Fundamentos de Programación

En este módulo aprenderás los conceptos básicos para escribir tus primeros programas en Java. 

---

## **1. Escribir tu Primer Programa**

El primer paso en programación es entender la estructura básica de un programa. Comenzaremos con el clásico "Hola Mundo":

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hola Mundo");
    }
}
```

### **Explicación del Código:**
1. `public class Main`: Declara una clase pública llamada `Main`. Todo el código en Java debe estar contenido en una clase.
2. `public static void main(String[] args)`: Este es el punto de entrada de cualquier programa en Java. Sin este método, el programa no se ejecutará.
3. `System.out.println("Hola Mundo");`: Imprime el mensaje en la consola.



### **Ejercicio 1: Modificar el mensaje**
1. Cambia el mensaje para que salude con tu nombre.
2. Ejemplo de salida esperada:
   ```
   ¡Hola, [Tu Nombre]!
   ```

---

## **2. Estructura Básica del Código**

Una buena estructura y estilo son fundamentales en programación, pero también es igual de importante entender que hace cada método y parte de código. Para esto tenemos los comentarios, que son una descripción que no infiere en el código, dejandonos explicar detalladamente lo que estamos haciendo y así poder ser más sencilla la lectura de código.

### **Comentarios**
- **Comentarios de línea:** Usan `//`. Ejemplo:
  ```java
  // Este es un comentario de línea
  System.out.println("Hola Mundo");
  ```
- **Comentarios de bloque:** Usan `/* ... */`. Ejemplo:
  ```java
  /*
   * Este es un comentario de bloque.
   */
  System.out.println("Hola Mundo");
  ```


### **Ejercicio 2: Añadir comentarios**
1. Añade comentarios explicando tu programa creado en el Ejercicio 1.

---

## **3. Tipos de Datos y Variables**

Las variables son contenedores para almacenar datos. En ellos, podremos almacenar información dependiendo de su tipado:

### **Tipos de Datos Primitivos**
- `int` o `long`: Números enteros.  Ejemplo:
  ```java
  int edad = 25;
  ```
  
- `float` o `double`: Números decimales. Ejemplo:
  ```java
  double altura = 1.75;
  ```

- `boolean`: Verdadero o falso. Ejemplo:
  ```java
  boolean esEstudiante = true;
  ```

- `char`: Carácter. Ejemplo:
  ```java
  char letra = 'j';
  char numero = '5';
  char simbolo = '?';
  ```


### **String**
Un `String` es un objeto en Java que representa una secuencia de caracteres.

```java
String saludo = "Hola Mundo";
```

#### **Operaciones comunes:**
- Concatenar cadenas:
  ```java
  String nombre = "Juan";
  String mensaje = "Hola " + nombre;
  System.out.println(mensaje); // Resultado: Hola Juan
  ```

### **Declaración de Variables**
```java
int numero = 10; // Declaración e inicialización de un int
numero = 20;     // Asignación posterior

String nombre = "Juan"; //Declaración e iniciación de un String
```

### **Constantes:**
Una constante es una variable que NUNCA podrá ser alterada, es decir, una vez se declare junto a su asignación de dato, NO PODRÁ CAMBIAR y será siempre lo asignado. Esto se realiza con la palabra `final`. Ejemplo:
```java
final int numero = 10; // Declaración e inicialización de una constante de tipo int y de valor 10. numero SIEMPRE valdrá 10.
numero = 20;     // Saltará error en la asignación posterior porque su valor siempre será 10
```

### **Ejercicio 3: Datos personales**
1. Crea variables para almacenar tu nombre, edad y ciudad. Imprímelas en consola y documenta tu código.

---
## **4. Convenciones de Nombres**

### **Buenas Prácticas:**
1. **Clases:** Usar **PascalCase** (Primera letra de cada palabra en mayúscula).
   - Ejemplo: `MiClase`, `CalculadoraSimple`.
2. **Variables y métodos:** Usar **camelCase** (Primera letra en minúscula, siguientes palabras con mayúscula).
   - Ejemplo: `miVariable`, `calcularArea`.
3. **Constantes:** Usar mayúsculas separadas por guiones bajos (`_`).
   - Ejemplo: `PI`, `MAX_VELOCITY`.

## **5. Operaciones y Expresiones**

### **Operadores Aritméticos**
- `+` (suma)
- `-` (resta)
- `*` (multiplicación)
- `/` (división)
- `%` (**módulo**: el **resto** de una división)
 
    - Ejemplo:
  ```java
  int suma = 5 + 3; // Resultado: 8
  int resto = 10 % 3; // Resultado: 1
  ```

### **Operadores Relacionales**
- `==` (igual a)
- `!=` (desigual a)
- `<` (menor a)
- `>` (mayor a)
- `<=` (menor o igual a)
- `>=` (mayor o igual a)

    - Ejemplo:
  ```java 
  boolean comparacion = (5 > 3); // true
  ```
  
### **Operadores Lógicos**
- `&&` (AND lógico): Devuelve `true` si ambas expresiones son verdaderas.

- `||` (OR lógico): Devuelve `true` si al menos una expresión es verdadera.
- `!` (NOT lógico): Invierte el valor de una expresión booleana (`true` a `false` y viceversa).

#### **Ejemplo:**
```java
boolean esAdulto = true;
boolean tienePermiso = false;

// AND lógico
boolean puedeEntrar = esAdulto && tienePermiso; // Resultado: false

// OR lógico
boolean puedeSalir = esAdulto || tienePermiso; // Resultado: true

// NOT lógico
boolean noTienePermiso = !tienePermiso; // Resultado: true
```

### **Operador Ternario**
El operador ternario es una forma abreviada de escribir un condicional `if-else`.

- Sintaxis:
  ```java
  condicion ? valor_si_true : valor_si_false;
  ```

#### **Ejemplo:**
```java
int edad = 18;
String mensaje = (edad >= 18) ? "Es mayor de edad" : "Es menor de edad";
System.out.println(mensaje); // Resultado: Es mayor de edad
```

### **Ejercicio 4: Operaciones matemáticas**
1. Crea un programa que realice las siguientes operaciones:
   - Suma de dos números enteros.
   - Compruebe si la suma es mayor que 20 y si es asi almacene en un **String** <"es mayor a 20">, sino que alamcene <"es menor a 20">.
   - Imprima por pantalla el resultado solo si es impar.

---


## **6. Entradas y Salidas de Datos (Ampliado)**

La clase `Scanner` es una herramienta poderosa en Java que permite leer datos de entrada del usuario desde la consola. Estos datos pueden ser de diferentes tipos: texto, números, etc.


### **Cómo usar la clase `Scanner`**

Para usar `Scanner`, primero debemos importarla desde el paquete `java.util`.

### **1. Importación y creación del objeto `Scanner`**
- **Importación:**  
  ```java
  import java.util.Scanner;
  ```
- **Creación del objeto:**  
  ```java
  Scanner <nombre> = new Scanner(System.in);
  ```
  - `System.in` indica que el objeto leerá los datos desde la entrada estándar (el teclado).
  
  - El `<nombre>` es complemtamente libre, y puedes usar el que tu quieras. Por conveniencia, se suele utilizar los siguientes nombres, pero tu puedes llamarlo como quieras:
    - `sc`
    - `teclado`
    - `scanner`


### **2. Métodos Principales de `Scanner`**

La clase `Scanner` proporciona diferentes métodos para leer datos según el tipo esperado:

| Método              | Tipo de dato que lee       | Ejemplo de uso                        |
|---------------------|----------------------------|---------------------------------------|
| `nextLine()`        | String (línea completa)   | `String nombre = scanner.nextLine();` |
| `next()`            | String (una palabra)      | `String palabra = scanner.next();`    |
| `nextInt()`         | int                       | `int edad = scanner.nextInt();`       |
| `nextDouble()`      | double                    | `double altura = scanner.nextDouble();` |
| `nextFloat()`       | float                     | `float peso = scanner.nextFloat();`   |
| `nextBoolean()`     | boolean                   | `boolean respuesta = scanner.nextBoolean();` |


### **3. Ejemplo Completo**
Aquí combinamos varios métodos de `Scanner` para leer datos de diferentes tipos:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        // Crear el objeto Scanner
        Scanner scanner = new Scanner(System.in);

        // Leer un String (línea completa)
        System.out.println("Introduce tu nombre: ");
        String nombre = scanner.nextLine();

        // Leer un int
        System.out.println("Introduce tu edad: ");
        int edad = scanner.nextInt();

        // Leer un double
        System.out.println("Introduce tu altura (en metros): ");
        double altura = scanner.nextDouble();

        // Mostrar los datos
        System.out.println("Hola, " + nombre + ". Tienes " + edad + " años y mides " + altura + " metros.");
    }
}
```

#### **Notas importantes:**
1. **Espacios y saltos de línea:**
   - Si usas `nextLine()` después de métodos como `nextInt()` o `nextDouble()`, puede haber problemas con el salto de línea pendiente en el búfer. Usa un `scanner.nextLine();` adicional para limpiar el búfer.
   ```java
   scanner.nextLine(); // Limpia el salto de línea pendiente
   ```

### **4. Ejercicio 5: Programa interactivo**

**Descripción:**
Crea un programa que:
1. Solicite al usuario su nombre, edad y ciudad.
2. Imprima un mensaje personalizado con esos datos.

---

## **7. Ejercicios Finales**

1. **Programa básico de datos personales:** Almacena por teclado el nombre, apellidos, edad y ciudad del usuario y imprimelos por pantalla en una sola línea.

2. **Calcula el área de:**
   - Triángulo: Pide por teclado la base y la altura.
   - Círculo: Pide por teclado el radio.
3. **Conversión de unidades:**
   - Convertir grados Celsius a Fahrenheit. (si no sabes como funciona la conversion, busca en Google)
4. **Evaluaciones y tablas:**
   - Determina si un número es par o impar.
   - Muestra la tabla de multiplicar de un número.
