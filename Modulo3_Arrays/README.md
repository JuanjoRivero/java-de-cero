# **Módulo 3: Arrays y Matrices**

En este módulo, aprenderás a trabajar con **arrays** y **matrices**, estructuras que permiten almacenar múltiples valores en una sola variable. También veremos cómo manipular estas estructuras y qué métodos útiles ofrece Java para trabajar con ellas.

---

## **1. ¿Qué es un Array?**
Un **array** (o arreglo) es una estructura de datos que almacena un conjunto de elementos del **mismo tipo** en posiciones consecutivas de memoria. Cada elemento se accede mediante un **índice**.

### **Características principales:**
- Todos los elementos del array deben ser del mismo tipo (ejemplo: todos enteros `int` o todos cadenas `String`).
- Los índices de los arrays comienzan en `0`.
- Los arrays tienen un tamaño fijo que se debe especificar al crearlos.

### **1.1. Declaración e inicialización de un Array**

#### **Declarar un Array:**
Para declarar un array, especificamos el tipo de datos, seguido por `[]` y el nombre del array.

```java
int[] numeros; // Declaración de un array de enteros
```

#### **Inicializar un Array:**
Un array debe inicializarse antes de usarlo. Esto significa asignarle un tamaño y, opcionalmente, valores.

```java
numeros = new int[5]; // Crea un array de tamaño 5
```

- Ahora `numeros` puede almacenar 5 valores enteros. Por defecto, estos valores serán `0`.

#### **Declarar e inicializar en una sola línea:**
```java
int[] numeros = {10, 20, 30, 40, 50}; // Array con valores iniciales
```

### **1.2. Acceder y modificar elementos en un Array**
Usamos el **índice** del array para acceder o modificar un elemento. Recordemos que el índice empieza en `0`.

```java
int[] numeros = {10, 20, 30, 40, 50};

// Acceder al tercer elemento (índice 2)
System.out.println(numeros[2]); // Imprime: 30

// Modificar el segundo elemento (índice 1)
numeros[1] = 25;
System.out.println(numeros[1]); // Imprime: 25
```

### **1.3. Iterar sobre un Array**
La manera más común de recorrer un array es usando un bucle `for`.

#### **Ejemplo:**
```java
int[] numeros = {10, 20, 30, 40, 50};

for (int i = 0; i < numeros.length; i++) {
    System.out.println("Elemento en índice " + i + ": " + numeros[i]);
}
```

#### **Salida:**
```
Elemento en índice 0: 10
Elemento en índice 1: 20
Elemento en índice 2: 30
Elemento en índice 3: 40
Elemento en índice 4: 50
```

### **Ejercicio 1: Sumando elementos de un array**
Crea un programa que:
1. Declare un array de enteros con los valores `{5, 10, 15, 20, 25}`.
2. Use un bucle `for` para calcular la suma de todos los elementos del array.
3. Imprima la suma total.


## **1.4 Iterar sobre un Array con `foreach`**

### **¿Qué es el bucle `foreach`?**
El bucle `foreach` es una forma sencilla de recorrer todos los elementos de un array en Java. Permite acceder a los valores directamente sin necesidad de utilizar índices.

---

### **Cómo funciona:**
1. **Recorre cada elemento del array.**
2. **Asigna cada elemento a una variable temporal.**
3. **Permite realizar acciones sobre esa variable temporal.**

### **Sintaxis:**
```java
for (tipo variable : array) {
    // Código para usar cada elemento
}
```

- **`tipo`**: El tipo de datos de los elementos del array (por ejemplo, `int`, `String`).
- **`variable`**: Una variable temporal que representa el valor actual del array.
- **`array`**: El array que estás recorriendo.

---

### **Ejemplo básico:**
```java
int[] numeros = {1, 2, 3, 4, 5};

for (int numero : numeros) {
    System.out.println("Número: " + numero);
}
```

#### **Salida:**
```
Número: 1
Número: 2
Número: 3
Número: 4
Número: 5
```

---

### **Nota importante:**
El bucle `foreach` es ideal para:
- Leer elementos del array.
- Evitar errores relacionados con índices.

**Pero:** No permite modificar los elementos del array directamente. Si necesitas modificar los valores, usa un bucle `for` clásico.

---

### **Ejercicios prácticos:**

1. **Imprimir elementos de un array:**
   - Declara un array de números `{10, 20, 30, 40, 50}`.
   - Usa un bucle `foreach` para imprimir cada número.

2. **Suma de elementos:**
   - Declara un array de enteros `{5, 10, 15}`.
   - Usa un bucle `foreach` para sumar todos los elementos y mostrar la suma total.

3. **Imprimir cadenas de texto:**
   - Declara un array de cadenas `{"hola", "mundo", "java"}`.
   - Usa un bucle `foreach` para imprimir cada palabra.

---

## **2. Métodos más utilizados para trabajar con Arrays**

Java proporciona la clase `Arrays` en el paquete `java.util`, que incluye varios métodos útiles para manipular arrays. A continuación, una tabla con los métodos más comunes:

| **Método**                  | **Descripción**                                                                 | **Ejemplo**                                         |
|-----------------------------|---------------------------------------------------------------------------------|---------------------------------------------------|
| `Arrays.toString(array)`    | Convierte un array en una cadena legible.                                        | `[1, 2, 3]`                                       |
| `Arrays.equals(array1, array2)` | Compara si dos arrays tienen el mismo contenido (elemento a elemento).         | `true` o `false`                                  |
| `Arrays.fill(array, valor)` | Llena todo el array con el mismo valor.                                          | `[5, 5, 5, 5]`                                    |
| `Arrays.sort(array)`        | Ordena los elementos del array en orden ascendente.                             | `[1, 2, 3, 4]`                                    |
| `Arrays.copyOf(array, n)`   | Crea una copia del array, ajustando el tamaño si es necesario.                   | `[1, 2, 3]` → `[1, 2, 3, 0, 0]`                  |
| `Arrays.copyOfRange(array, inicio, fin)` | Copia un rango de elementos del array original (excluye el índice `fin`). | `[1, 2, 3, 4, 5]` → `[2, 3]`                     |
| `Arrays.binarySearch(array, valor)` | Busca un valor en un array ordenado y devuelve su índice (o un valor negativo si no se encuentra). | `3` (si `valor` está en el índice 3)             |

---

## **Desglose de métodos**

### **1. `Arrays.toString(array)`**
Convierte un array en una representación de cadena para que sea más legible al imprimirlo.

#### **Ejemplo:**
```java
import java.util.Arrays;

int[] numeros = {1, 2, 3};
System.out.println(Arrays.toString(numeros)); // Salida: [1, 2, 3]
```

---

### **2. `Arrays.equals(array1, array2)`**
Compara si dos arrays son iguales, verificando que tengan el mismo tamaño y los mismos elementos en el mismo orden.

#### **Ejemplo:**
```java
import java.util.Arrays;

int[] a = {1, 2, 3};
int[] b = {1, 2, 3};
int[] c = {3, 2, 1};

System.out.println(Arrays.equals(a, b)); // Salida: true
System.out.println(Arrays.equals(a, c)); // Salida: false
```

---

### **3. `Arrays.fill(array, valor)`**
Llena un array completo con un valor específico.

#### **Ejemplo:**
```java
import java.util.Arrays;

int[] numeros = new int[5];
Arrays.fill(numeros, 7); // Llena el array con el valor 7
System.out.println(Arrays.toString(numeros)); // Salida: [7, 7, 7, 7, 7]
```

---

### **4. `Arrays.sort(array)`**
Ordena un array en orden ascendente.

#### **Ejemplo:**
```java
import java.util.Arrays;

int[] numeros = {5, 3, 8, 1};
Arrays.sort(numeros); // Ordena el array
System.out.println(Arrays.toString(numeros)); // Salida: [1, 3, 5, 8]
```

---

### **5. `Arrays.copyOf(array, n)`**
Crea una copia del array con un tamaño especificado. Si el tamaño nuevo es mayor, los elementos faltantes se llenan con valores predeterminados (`0` para enteros, `null` para objetos).

#### **Ejemplo:**
```java
import java.util.Arrays;

int[] numeros = {1, 2, 3};
int[] copia = Arrays.copyOf(numeros, 5); // Crea una copia con tamaño 5
System.out.println(Arrays.toString(copia)); // Salida: [1, 2, 3, 0, 0]
```

---

### **6. `Arrays.copyOfRange(array, inicio, fin)`**
Copia un rango de elementos de un array. El índice `inicio` está incluido, pero `fin` no.

#### **Ejemplo:**
```java
import java.util.Arrays;

int[] numeros = {1, 2, 3, 4, 5};
int[] rango = Arrays.copyOfRange(numeros, 1, 4); // Copia elementos de índice 1 a 3
System.out.println(Arrays.toString(rango)); // Salida: [2, 3, 4]
```

---

### **7. `Arrays.binarySearch(array, valor)`**
Busca un valor en un array ordenado y devuelve su índice. Si no se encuentra, devuelve un valor negativo.

#### **Ejemplo:**
```java
import java.util.Arrays;

int[] numeros = {1, 3, 5, 7, 9};
System.out.println(Arrays.binarySearch(numeros, 5)); // Salida: 2
System.out.println(Arrays.binarySearch(numeros, 6)); // Salida: -4 (no encontrado)
```

---

### **Ejercicio práctico:**
1. **Copiar y ampliar un array:**
   - Declara un array de enteros `{2, 4, 6, 8}`.
   - Crea una copia con tamaño 6 y llena los nuevos espacios con `0`.
   - Ordenalo.
   - Imprime el nuevo array.

2. **Rango de copia:**
   - Declara un array de enteros `{10, 20, 30, 40, 50}`.
   - Copia los elementos desde el índice 2 al 4.
   - Imprime el array resultante.
   - Imprime el índice del valor "30" almacenado en el array.

3. **Comparar dos arrays**

    - Declara dos arrays de enteros de igual tamaño.
    - Llena ambos arrays con valores introducidos por el usuario.
    - Comprueba si ambos arrays tienen el mismo contenido.
    - Imprime un mensaje indicando si los arrays son iguales o diferentes.
---

## **3. ¿Qué es una Matriz (Array Multidimensional)?**

Una matriz es un array de arrays, o una tabla bidimensional. Cada fila puede ser vista como un array individual.

### **3.1. Declarar e inicializar una Matriz**
#### **Declaración:**
```java
int[][] matriz; // Declaración de una matriz de enteros
```

#### **Inicialización:**
```java
matriz = new int[2][3]; // 2 filas, 3 columnas
```

#### **Declaración e inicialización directa:**
```java
int[][] matriz = {
    {1, 2, 3}, 
    {4, 5, 6}
};
```

### **3.2. Acceder y modificar elementos en una Matriz**
Usamos dos índices: uno para la fila y otro para la columna.

#### **Ejemplo:**
```java
int[][] matriz = {
    {1, 2, 3}, 
    {4, 5, 6}
};

// Acceder al elemento en la fila 1, columna 2
System.out.println(matriz[1][2]); // Imprime: 6

// Modificar el elemento en la fila 0, columna 1
matriz[0][1] = 9;
System.out.println(matriz[0][1]); // Imprime: 9
```

### **3.3. Iterar sobre una Matriz**
Para recorrer una matriz, usamos bucles anidados.

#### **Ejemplo:**
```java
int[][] matriz = {
    {1, 2, 3}, 
    {4, 5, 6}
};

for (int i = 0; i < matriz.length; i++) { // Recorre las filas
    for (int j = 0; j < matriz[i].length; j++) { // Recorre las columnas
        System.out.println("Elemento en [" + i + "][" + j + "]: " + matriz[i][j]);
    }
}
```

#### **Salida:**
```
Elemento en [0][0]: 1
Elemento en [0][1]: 2
Elemento en [0][2]: 3
Elemento en [1][0]: 4
Elemento en [1][1]: 5
Elemento en [1][2]: 6
```

### **Ejercicio 3: Suma de una matriz**
Crea un programa que calcule la suma de todos los elementos en una matriz de enteros de tamaño 3x3.

---


## **Ejercicios Prácticos**

### **Nivel Básico**

1. **Multiplicación de elementos de un array:**
   - Declara un array de enteros `{1, 2, 3, 4, 5}`.
   - Usa un bucle `for` para calcular el producto de todos los elementos del array.
   - Imprime el resultado.

2. **Invertir un array:**
   - Crea un programa que pida al usuario 5 números y los almacene en un array.
   - Usa un bucle para imprimir los elementos del array en orden inverso.

3. **Buscar un elemento en un array:**
   - Declara un array de enteros `{10, 20, 30, 40, 50}`.
   - Pide al usuario un número y busca si está en el array.
   - Si el número está en el array, imprime su índice. Si no, muestra un mensaje indicando que no se encontró.
   
4. **Notas de estudiantes:**
   - Escribe un programa que almacene las notas de 5 estudiantes en un array y calcule la media.
   
5. **Valor máximo y mínimo:**
   - Encuentra el valor más alto y el más bajo en un array de números.

---

### **Nivel Intermedio**

1. **Concatenar dos arrays:**
   - Declara dos arrays de enteros de igual tamaño, por ejemplo `{1, 2, 3}` y `{4, 5, 6}`.
   - Crea un tercer array que combine los elementos de ambos arrays en el mismo orden.
   - Imprime el nuevo array.

2. **Calcular promedios de filas en una matriz:**
   - Declara una matriz de tamaño 3x3:
     ```java
     int[][] matriz = {
         {10, 20, 30},
         {40, 50, 60},
         {70, 80, 90}
     };
     ```
   - Calcula e imprime el promedio de los valores de cada fila.

3. **Eliminar duplicados en un array:**
   - Declara un array de enteros `{1, 2, 2, 3, 4, 4, 5}`.
   - Crea un programa que elimine los valores duplicados y genere un nuevo array sin ellos.
   - Imprime el nuevo array.

---

### **Nivel Avanzado**

1. **Rotar una matriz:**
   - Declara una matriz de tamaño 3x3:
     ```java
     int[][] matriz = {
         {1, 2, 3},
         {4, 5, 6},
         {7, 8, 9}
     };
     ```
   - Escribe un programa que rote la matriz 90 grados en el sentido de las agujas del reloj.
   - Imprime la matriz resultante.

2. **Multiplicación de dos matrices:**
   - Declara dos matrices de tamaño 2x2:
     ```java
     int[][] matriz1 = {
         {1, 2},
         {3, 4}
     };

     int[][] matriz2 = {
         {5, 6},
         {7, 8}
     };
     ```
   - Calcula el producto de ambas matrices y almacena el resultado en una tercera matriz.
   - Imprime la matriz resultante.

3. **Spiral traversal de una matriz:**
   - Declara una matriz de tamaño 4x4:
     ```java
     int[][] matriz = {
         {1, 2, 3, 4},
         {5, 6, 7, 8},
         {9, 10, 11, 12},
         {13, 14, 15, 16}
     };
     ```
   - Crea un programa que imprima los elementos de la matriz en un recorrido en espiral (desde el borde exterior hacia el interior).
