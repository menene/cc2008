# Datos y Expresiones
Semestre 02, 2025



## Cadenas (Strings)


Una cadena puede contener cualquier carácter válido, incluyendo números, signos de puntuación y otros símbolos.  
Se escribe entre **comillas dobles**.


Ejemplos:
```
"Hola, mundo!"
"10 de octubre de 2012"
""
```


Una cadena vacía es válida: `""`


En Java, las cadenas pertenecen a la clase **`String`**.


### Concatenación de cadenas


```java
System.out.print("Hola");
System.out.println(" Mundo!");
```
- `System.out.print()` no avanza de línea.  
- `System.out.println()` imprime y luego hace salto de línea.


### El operador +

El operador `+` se usa para concatenar cadenas.

```java
System.out.println("24 and 45 concatenated: " + 24 + 45);
```
Resultado:  
```
24 and 45 concatenated: 2445
```


Para sumar valores numéricos:
```java
System.out.println("24 and 45 added: " + (24 + 45));
```
Resultado:  
```
24 and 45 added: 69
```



## Secuencias de escape


Java tiene **secuencias de escape** para representar caracteres especiales dentro de cadenas.


| Secuencia | Significado      |
|-----------|------------------|
| `\b`     | backspace        |
| `\t`     | tabulación       |
| `\n`     | nueva línea      |
| `\r`     | retorno de carro |
| `\"`     | comilla doble    |
| `\'`     | comilla simple   |
| `\\`    | barra invertida  |


Ejemplo:
```java
System.out.println("Hola\nMundo");
```



## Variables y tipos de datos


Una **variable** es un nombre para una ubicación en memoria que almacena datos.


Declaración:
```java
int total;
double precio;
char letra;
```


Se pueden declarar múltiples variables del mismo tipo:
```java
int x, y, z;
```



### Constantes


- Se declaran con la palabra clave `final`.  
- Por convención, se escriben en **mayúsculas**.


```java
final int MAX_USERS = 100;
```



## Tipos de datos primitivos


| Tipo    | Tamaño   | Valor mínimo      | Valor máximo       |
|---------|----------|--------------------|--------------------|
| byte    | 8 bits   | -128               | 127                |
| short   | 16 bits  | -32,768            | 32,767             |
| int     | 32 bits  | -2.1×10⁹           | 2.1×10⁹            |
| long    | 64 bits  | -9×10¹⁸            | 9×10¹⁸             |
| float   | 32 bits  | -3.4×10³⁸ (7 dec)  | +3.4×10³⁸ (7 dec)  |
| double  | 64 bits  | -1.7×10³⁰⁸ (15 dec)| +1.7×10³⁰⁸ (15 dec)|



## Caracteres y Unicode


- El tipo **`char`** representa un solo carácter Unicode.  


```java
char letra = 'A';
```


- Unicode: [Unicode](https://symbl.cc/en/unicode-table/)



## Booleanos


El tipo **`boolean`** solo acepta dos valores:
- `true`
- `false`


```java
boolean activo = true;
```


Usado para condiciones y control de flujo.



## Operadores aritméticos

| Operador | Descripción        |
|----------|--------------------|
| `+`      | Suma               |
| `-`      | Resta              |
| `*`      | Multiplicación     |
| `/`      | División           |
| `%`      | Residuo (módulo)   |


### Precedencia de operadores (PEMDASA)


```java
int result = 14 + 8 / 2;         // 18
int result2 = 3 * ((18 - 4) / 2); // 21
```



## Operadores de incremento y decremento


```java
count++;   // Incrementa en 1 (postfijo)
++count;   // Incrementa en 1 (prefijo)
```


Equivalente a:
```java
count = count + 1;
```



## Asignación compuesta


| Operador | Ejemplo      | Equivalente         |
|----------|--------------|----------------------|
| `+=`     | `x += y;`    | `x = x + y;`         |
| `-=`     | `x -= y;`    | `x = x - y;`         |
| `*=`     | `x *= y;`    | `x = x * y;`         |
| `/=`     | `x /= y;`    | `x = x / y;`         |
| `%=`     | `x %= y;`    | `x = x % y;`         |



## Conversiones de tipo (Casting)


### Conversión implícita (widening)


```java
int num = 10;
double result = num / 3; // int → double
```


### Conversión explícita (narrowing)


```java
double value = 9.8;
int truncated = (int) value; // 9
```



## Entrada de datos con Scanner


```java
import java.util.Scanner;

Scanner teclado = new Scanner(System.in);

System.out.print("Ingrese su nombre: ");
String nombre = teclado.nextLine();

System.out.println("Hola " + nombre + "!");
```



### Notas sobre Scanner

- `nextLine()` → lee línea completa
- `nextInt()`, `nextDouble()` → leen números
- Ignora espacios en blanco automáticamente como separadores