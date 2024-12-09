# **Módulo 2: Control de Flujo**

En este módulo aprenderás cómo los programas toman decisiones y repiten acciones. Esto es esencial para escribir código dinámico que se adapte a diferentes escenarios.

---

## **1. Estructuras Condicionales**

Las estructuras condicionales son la forma en que le decimos a un programa: **“Si pasa esto, haz esto otro; si no, haz algo diferente”**. Es como tomar decisiones en la vida cotidiana.

### **1.1. if, else if, else**
- **¿Qué hace?**  
  Evalúa una condición. Si la condición es verdadera (`true`), ejecuta un bloque de código. Si es falsa (`false`), pasa al siguiente bloque o no ejecuta nada.

#### **Explicación paso a paso:**
1. **El programa evalúa la condición.**
2. **Si la condición es verdadera**, ejecuta el código dentro del bloque `{ }` inmediatamente después del `if`.
3. **Si es falsa y existe un `else if`**, evalúa esa nueva condición.
4. **Si todas las condiciones son falsas y hay un `else`**, ejecuta el bloque del `else`.

#### **Ejemplo básico:**
```java
int edad = 18;

// El programa verifica cada condición en orden
if (edad < 18) {
    System.out.println("Menor de edad"); // Esto se ejecuta si edad es menor a 18
} else if (edad == 18) {
    System.out.println("Recién mayor de edad"); // Esto se ejecuta si edad es exactamente 18
} else {
    System.out.println("Mayor de edad"); // Esto se ejecuta si edad es mayor a 18
}
```

#### **Salida:**
Si `edad` es 18, el resultado será:  
```
Recién mayor de edad
```

### **1.2. switch**
- **¿Qué hace?**  
  Evalúa el valor de una variable y ejecuta el bloque de código correspondiente al caso que coincide. Es ideal cuando tienes múltiples opciones (como un menú).

#### **Cómo funciona?**
1. **El programa compara el valor de la variable con los valores de los `case`.**
2. **Cuando encuentra una coincidencia**, ejecuta el código de ese `case`.
3. Si no encuentra coincidencia, ejecuta el bloque `default` (si existe).
4. Cada `case` debe terminar con `break` para evitar que el programa siga ejecutando los demás casos.

#### **Ejemplo básico:**
```java
int opcion = 2;

switch (opcion) {
    case 1:
        System.out.println("Opción 1 seleccionada");
        break; // Salta fuera del switch
    case 2:
        System.out.println("Opción 2 seleccionada");
        break;
    default:
        System.out.println("Opción no válida");
}
```

#### **Salida:**
Si `opcion` es 2, el resultado será:  
```
Opción 2 seleccionada
```

### **Ejercicio práctico: Sistema de calificaciones**
1. Crea un programa que reciba una nota entre 0 y 100.
2. Usa `if-else` para imprimir:
   - "Aprobado" si la nota está entre 60 y 100.
   - "Reprobado" si la nota está entre 0 y 59.

---

## **2. Bucles**

Los bucles permiten repetir acciones. Son útiles cuando necesitamos procesar listas, contar números, o realizar tareas repetitivas.

### **2.1. for**
- **¿Qué hace?**  
  Ejecuta un bloque de código un número fijo de veces. Es ideal cuando conoces de antemano cuántas veces quieres repetir algo.

#### **Partes de un `for`:**
1. **Inicialización:** Define una variable (ej. `int i = 0`).
2. **Condición:** Evalúa si el bucle debe continuar (ej. `i < 10`).
3. **Actualización:** Cambia la variable tras cada iteración (ej. `i++`).

#### **Ejemplo básico:**
```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Iteración: " + i);
}
```

#### **Salida:**
```
Iteración: 1
Iteración: 2
Iteración: 3
Iteración: 4
Iteración: 5
```

### **2.2. while**
- **¿Qué hace?**  
  Ejecuta un bloque de código mientras una condición sea verdadera.

#### **Cómo funciona?**
1. Verifica la condición antes de cada iteración.
2. Si la condición es `true`, ejecuta el código dentro del bloque.
3. Si la condición es `false`, el bucle termina.

#### **Ejemplo básico:**
```java
int contador = 1;

while (contador <= 3) {
    System.out.println("Contador: " + contador);
    contador++; // Incrementa el contador
}
```

#### **Salida:**
```
Contador: 1
Contador: 2
Contador: 3
```

---

### **2.3. do-while**
- **¿Qué hace?**  
  Similar a `while`, pero **siempre ejecuta el bloque al menos una vez**, ya que la condición se evalúa al final.

#### **Ejemplo básico:**
```java
int numero = 10;

do {
    System.out.println("Número: " + numero);
    numero--; // Disminuye el valor de número
} while (numero > 0);
```

#### **Salida:**
```
Número: 10
Número: 9
...
Número: 1
```

### **Ejercicio práctico: Contar impares**
Usa un `while` para imprimir los números impares del 1 al 50.

---

## **3. Saltos en Bucles**

### **3.1. break**
- **¿Qué hace?**  
  Detiene el bucle inmediatamente, sin importar la condición.

#### **Ejemplo:**
```java
for (int i = 0; i < 10; i++) {
    if (i == 5) break; // Sale del bucle cuando i es 5
    System.out.println(i);
}
```

#### **Salida:**
```
0
1
2
3
4
```

### **3.2. continue**
- **¿Qué hace?**  
  Salta el resto del código en la iteración actual y pasa a la siguiente.

#### **Ejemplo:**
```java
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) continue; // Salta números pares
    System.out.println(i);
}
```

#### **Salida:**
```
1
3
5
7
9
```

### **Ejercicio práctico: FizzBuzz**
Imprime números del 1 al 20:
- Si es divisible por 3, imprime "Fizz".
- Si es divisible por 5, imprime "Buzz".
- Si es divisible por ambos, imprime "FizzBuzz".

---

## **Ejercicios Prácticos**
Para practicar un poco, mejorar la lógica de programación y ver los conocimientos obtenidos, te paso una serie de ejercicios clasificados por niveles para poder entrenarte:

### **Nivel Básico**
1. **Números pares:**
   - Escribe un programa que use un bucle `for` para imprimir todos los números pares entre 1 y 50.

2. **Contador inverso:**
   - Usando un bucle `while`, crea un programa que cuente desde 10 hasta 1 e imprima cada número.

3. **Calificación de exámenes:**
   - Escribe un programa que solicite al usuario una nota entre 0 y 100. Usa un `if-else` para clasificar la nota como:
     - 0-59: "Reprobado"
     - 60-79: "Aprobado"
     - 80-100: "Excelente"

---

### **Nivel Intermedio**
1. **Menú interactivo:**
   - Crea un programa que presente un menú de opciones al usuario:
     - 1. Sumar dos números
     - 2. Restar dos números
     - 3. Salir del programa  
   - Usa un `switch` para procesar la opción elegida. Debes permitir al usuario ingresar los números cuando sea necesario.

2. **Serie Fibonacci:**
   - Escribe un programa que pida al usuario un número entero `n` y genere la serie de Fibonacci hasta el `n`-ésimo término. Usa un bucle `for`.

3. **Impares con continue:**
   - Usa un `for` para imprimir los números del 1 al 20. Si el número es par, salta esa iteración usando `continue`.

---

### **Nivel Avanzado**

1. **Juego de adivinanza:**
   - Escribe un programa que genere un número aleatorio entre 1 y 100.
   - Permite al usuario intentar adivinarlo, mostrando pistas como "Más alto" o "Más bajo" después de cada intento.
   - Usa un bucle `do-while` para continuar el juego hasta que el usuario adivine correctamente.

2. **Número perfecto:**
   - Crea un programa que determine si un número dado por el usuario es un número perfecto.
   - Un número perfecto es aquel cuya suma de sus divisores propios (excluyendo el número en sí) es igual al número. Ejemplo: 6 es perfecto porque sus divisores son 1, 2, y 3, y \(1 + 2 + 3 = 6\).

---

#### **Notas para todos los ejercicios**
- Asegúrate de usar **comentarios** para explicar qué hace cada parte del código.
- Experimenta con **valores de prueba** para validar tus soluciones.
- Si algún ejercicio resulta difícil, desglósalo en pasos más pequeños (pseudocódigo). 