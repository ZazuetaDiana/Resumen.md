
![](https://images.cooltext.com/5474769.png)
<a href="http://cooltext.com" target="_top"><img src="https://cooltext.com/images/ct_pixel.gif" width="80" height="15" alt="Cool Text: Logo and Graphics Generator" border="0" /></a>

***Introducción al ensamblador***
-------------------------------

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

**Modos de direccionamiento del ARM
---------
En la arquitectura ARM los accesos a memoria se hacen mediante instrucciones específicas ldr y str .El resto de instrucciones toman operandos desde registros o valores inmediatos, sin excepciones

**La arquitectura nos fuerza a que trabajemos de una forma determinado:**

-	1. Cargamos los registros desde memoria.
-	2. Procesamos el valor de estos registros con el amplio abanico de instrucciones del ARM.
-	3. Volcar los resultados desde registros a memoria.

Existen otras arquitecturas como la Intel x86, donde las instrucciones de procesado nos permiten leer o escribir directamente de memoria.



