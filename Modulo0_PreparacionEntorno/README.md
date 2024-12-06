# Módulo 0: Preparación del entorno

En este módulo aprenderás a instalar y configurar dos herramientas clave para programar en Java: **Git** e **IntelliJ IDEA**.

---

## **1. Instalación de Git**
Git es una herramienta de control de versiones que nos permite gestionar nuestros proyectos.

### **Pasos para instalar Git**
1. Accede a la página oficial de Git: [git-scm.com](https://git-scm.com/).
2. Descarga la versión adecuada para tu sistema operativo.
3. Sigue el asistente de instalación. Asegúrate de:
   - Seleccionar "Use Git from the command line and also from 3rd-party software".
4. Verifica la instalación abriendo una terminal y escribiendo:
   ```bash
   git --version
   ```
### **Comandos básicos de Git**
- `git add <archivo> / <ruta>`: Añade cambios al área de preparación.
- `git commit -m "mensaje"`: Guarda los cambios con un mensaje descriptivo.
- `git status`: Muestra el estado del repositorio.
- `git push`: Sube los cambios guardados que has "comiteado".

---

## **2. Instalación de IntelliJ IDEA**
IntelliJ IDEA es un entorno de desarrollo (IDE) que facilita la programación en Java.

### **Pasos para instalar IntelliJ**
1. Visita [jetbrains.com/idea](https://www.jetbrains.com/idea/).
2. Descarga la versión **Community** (gratuita).
3. Sigue el asistente de instalación.
4. Abre IntelliJ y selecciona:
   - **Create New Project** para iniciar un proyecto desde cero.
   - Configura el SDK de Java descargando [JDK](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) 21. Es importante que la versión sea la 21 porque es la que vamos a utilizar a lo largo del curso.

---

## **Práctica**
1. Crea un repositorio Git en tu computadora:
   ```bash
   mkdir CursoJava
   cd CursoJava
   git init
   ```
2. Crea un nuevo proyecto en IntelliJ:
   - Nombre del proyecto: **HolaMundo**.
   - Clase principal: `Main.java`.

3. Escribe tu primer programa en Java:
   ```java
   public class Main {
       public static void main(String[] args) {
           System.out.println("¡Hola Mundo!");
       }
   }
   ```
4. Ejecuta el programa presionando el botón verde en IntelliJ.

---

¡Tu entorno está listo para comenzar a programar!
