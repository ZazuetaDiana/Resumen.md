
![](https://images.cooltext.com/5474769.png)
<a href="http://cooltext.com" target="_top"><img src="https://cooltext.com/images/ct_pixel.gif" width="80" height="15" alt="Cool Text: Logo and Graphics Generator" border="0" /></a>

***Introducción al ensamblador***
-------------------------------
**Características generales de la arquitectura ARM**

ARM es una arquitectura RISC de 32 bits, salvo la versión del core ARMv8- A que es mixta 32/64 bits. Se trata de una arquitectura licenciable, quiere decir que la empresa desarrolladora ARM Holdings diseña la arquitectura, pero son otras compañías las que fabrican y venden los chips, llevándose ARM Holdings un pequeño porcentaje por la licencia.


Existen 16 registros principales de arquitectura ARM ,13 registros generales que su función es el almacenamiento temporal de datos, que van R0 hasta R12. Y los últimos 3 registros especiales, que van de R13, R14 y R15, son de propósito especial, tienen nombres alternativos.

- SP/R13. Stack Pointer ó Puntero de Pila. Sirve como puntero para almacenar variables locales y registros en llamadas a funciones.
- LR/R14. Link Register ó Registro de Enlace. Almacena la dirección de retorno cuando una instrucción BL ó BLX ejecuta una llamada a una rutina.
- PC/R15. Program Counter ó Contador de Programa. Es un registro que indica la posición donde está el procesador en su secuencia de instrucciones. Se incrementa de 4 en 4 cada vez que se ejecuta una instrucción, salvo que ésta provoque un salto.

Registro CPSR. Almacena las banderas condicionales y los bits de control.

**Existen 4 banderas:**

- N. Se activa cuando el resultado es negativo.
- Z. Se activa cuando el resultado es cero o una comparación es cierta. 
- C. Indica acarreo en las operaciones aritméticas. 
- V. Desbordamiento aritmético.

**Esquema de almacenamiento**
La regla que sigue es ***“el byte menos significativo ocupa la posición más baja”.***


***Ubicación en memoria***

![](https://github.com/ZazuetaDiana/Resumen.md/blob/main/imagen1png.png)

**El lenguaje ensamblador**

Es de bajo nivel, permite un control directo de la CPU y todos los elementos asociados. Cada línea de un programa ensamblador consta de una instrucción del procesador y la posición que ocupan los datos de esa instrucción.
Un conjunto de instrucciones y/o datos forman un módulo fuente. Este módulo es la entrada del compilador, que chequea la sintaxis y lo traduce a código máquina formando un módulo objeto. Finalmente, un enlazador (montador ó linker) traduce todas las referencias relativas a direcciones absolutas y termina generando el ejecutable.

***Ventajas***

- Flexibilidad.  

- Posibilidad de acceso directo a nivel de registro.

***Desventajas***

- Desarrollar programas en este es un proceso laborioso.

-  Corrección y depuración de éstos se hace difícil.


-----------------------------------

***Entorno típico de programación***

![](https://github.com/ZazuetaDiana/Resumen.md/blob/main/imagen2.png)

**2 Tipos de errores durante la creación de un programa:**

-	Sintácticos o detectables: en tiempo de traducción.
-	Semánticos o detectables: en tiempo de ejecución. 

**La estructura más general de un módulo fuente es:**

 - Sección de datos: Viene identificada por la directiva .data.
- Sección de código: Se indica con la directiva .text, y sólo puede contener código o datos no modificables. 


Modos de direccionamiento del ARM
---------
En la arquitectura ARM los accesos a memoria se hacen mediante instrucciones específicas ldr y str .El resto de instrucciones toman operandos desde registros o valores inmediatos, sin .

**La arquitectura nos fuerza a que trabajemos de una forma determinado:**

-	1. Cargamos los registros desde memoria.
-	2. Procesamos el valor de estos registros con el amplio abanico de instrucciones del ARM.
-	3. Volcar los resultados desde registros a memoria.

Existen otras arquitecturas como la Intel x86, donde las instrucciones de procesado nos permiten leer o escribir directamente de memoria.

**Direccionamiento inmediato.**

 El operando fuente es una constante, formando parte de la instrucción.
 
 ![](https://github.com/ZazuetaDiana/Resumen.md/blob/main/imagen3.png)
 
 
**Direccionamiento inmediato con desplazamiento o rotación.**

Es una variante del anterior en la cual se permiten operaciones intermedias sobre los registros.

![](https://github.com/ZazuetaDiana/Resumen.md/blob/main/imagen4.png)

**Direccionamiento a memoria, sin actualizar registro puntero.**

 Es la forma más sencilla y admite 4 variantes. Después del acceso a memoria ningún registro implicado en el cálculo de la dirección se modifica
 
**Direccionamiento a memoria, actualizando registro puntero.**

El registro que genera la dirección se actualiza con la propia dirección. De esta forma podemos recorrer un array con un sólo registro sin necesidad de hacer el incremento del puntero en una instrucción aparte.

**Tipos de datos**

![](https://github.com/ZazuetaDiana/Resumen.md/blob/main/imagen5.png)

**Punteros.**

 Un puntero siempre ocupa 32 bits y contiene una dirección de memoria. En ensamblador no tienen tanta utilidad como en C, ya que disponemos de registros de sobra y es más costoso acceder a las variables a través de los punteros que directamente.  
 
**Vectores.**

Todos los elementos de un vector se almacenan en un único bloque de memoria a partir de una dirección determinada.
**Matrices bidimensionales. **

Una matriz bidimensional de N×M elementos se almacena en un único bloque de memoria. Interpretaremos una matriz de N×M como una matriz con N filas de M elementos cada una.

**Instrucciones de salto**

Pueden producir saltos incondicionales (b y bx) o saltos condicionales. Cuando saltamos a una etiqueta empleamos b, mientras que si queremos saltar a un registro lo hacemos con bx. La variante de registro bx la solemos usar como instrucción de retorno de subrutina, raramente tiene otros usos

**Compilación a ensamblador**

 Normalmente los compiladores en C real crean código compilado (archivos .o) en un único paso. En el caso de gcc este proceso se hace en dos fases: en una primera se pasa de C a ensamblador, y en una segunda de ensamblador a código compilado (código máquina). Lo interesante es que podemos interrumpir justo después de la compilación y ver con un editor el aspecto que tiene el código ensamblador generado a partir del código fuente en C.

![](https://images.cooltext.com/5474822.png)
<a href="http://cooltext.com" target="_top"><img src="https://cooltext.com/images/ct_pixel.gif" width="80" height="15" alt="Cool Text: Logo and Graphics Generator" border="0" /></a>

![](https://github.com/ZazuetaDiana/Resumen.md/blob/main/Ejercicio.png)

