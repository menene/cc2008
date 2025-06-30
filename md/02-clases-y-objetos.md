# Clases y Objetos
Semestre 02, 2025



## Clases


Una **clase** es una plantilla o molde para crear objetos.

Define:
- Atributos (Estado)
- Métodos (Comportamiento)


**Analogías:**
- Plano de una casa.
- Molde de galletas.



## Objetos


Un **objeto** es una entidad que tiene:
- **Atributos** (estado, propiedades)
- **Comportamientos** (acciones, métodos)


### Instancia
Creado en base a una clase.


Representa algo **concreto** del mundo real o algo **abstracto** en el sistema.


Ejemplos:
- Un bombillo tiene estado (encendido/apagado) y acciones (encender/apagar)
- Una cuenta bancaria tiene saldo y puede depositar o retirar dinero


### Usos
- Para **organizar** el código de forma modular
- Para **reutilizar** el código
- Para **modelar** el mundo real en un sistema


Ejemplo:
Clase `CuentaBancaria`
- Objetos: cuenta de Juan, cuenta de María, cuenta de Pedro


### Clase vs Objeto
**Clase:** estructura común
```
CuentaBancaria
- saldo: double
- depositar(monto: double)
- retirar(monto: double)
```

**Objeto:** instancia concreta
```
cuentaJuan → saldo = Q500.00
cuentaMaria → saldo = Q1500.00
```



## Anatomía de una Clase


### Estructura básica de una clase
```java []
public class Bombillo {
    // Atributos
    private boolean encendido;

    // Constructor
    public Bombillo() {
        encendido = false;
    }

    // Métodos
    public void encender() {
        encendido = true;
    }
}
```


### Constructores
- Método especial que se ejecuta al crear el objeto
- Nombre igual a la clase
- Se puede sobrecargar

```java []
public Cuenta(String nombre) {
    this.nombre = nombre;
}
```


### Métodos
- Definen comportamiento del objeto
- Partes:
  - Modificador de visibilidad
  - Tipo de retorno
  - Nombre
  - Parámetros

```java []
public void depositar(double monto) {
    saldo += monto;
}
```


### Visibilidad
  - `private`: solo accesible dentro de la clase
  - `public`: accesible desde cualquier parte
  - `protected`: Más adelante cuando veamos herencia.

```java []
private String nombre;
public int contador = 0;
```


### Encapsulamiento
- Encapsular = proteger el estado interno
- Seguridad
- Flexibilidad


Se usan `getters` y `setters`

```java []
public double getSaldo() {
    return saldo;
}

public void setSaldo(double nuevoSaldo) {
    saldo = nuevoSaldo;
}
```



## Anatomía de un Método


### Partes de un método
```java []
public double calcularArea(double base, double altura) {
    return base * altura;
}
```
- Modificador: `public`
- Tipo de retorno: `double`
- Nombre: `calcularArea`
- Parámetros: `base`, `altura`
- Cuerpo: instrucciones


### Ejemplo
```java []
public class Bombillo {
    public void encender() {
        System.out.println("Bombillo encendido");
    }
}
```



## UML


### Definición
- UML = Unified Modeling Language
- Herramienta para representar gráficamente:
  - Clases
  - Objetos
  - Relaciones


### Diagrama de clase básico
```
+----------------------+
| CuentaBancaria       |
+----------------------+
| - saldo: double      |
| - numero: Int        |
+----------------------+
| + depositar(monto)   |
| + retirar(monto)     |
+----------------------+
```


Clase: `CuentaBancaria`
-------------------------
Atributos:
- `- saldo: double`
- `- nombre: String`


Métodos:
- `+ getSaldo(): double`
- `+ depositar(monto: double): void`
- `+ retirar(monto: double): void`