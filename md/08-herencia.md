# Herencia
Semestre 2, 2025



## Usos


Reutilización de código: evita duplicación.


Modelado natural de jerarquías: ejemplo, **Animal → Perro → Pastor Alemán**.


Extensibilidad: se pueden crear nuevas clases a partir de otras ya existentes.


Permite **polimorfismo**.


La palabra **polimorfismo** proviene del griego poly (muchos) y morphé (formas). En Java, significa que un mismo objeto puede adoptar múltiples formas dependiendo del contexto de uso.


**Comparación con composición:**

* **Herencia:** modela relación “es-un” (is-a).
* **Composición:** modela relación “tiene-un” (has-a).



## Concepto


"¡Tan linda tu hija! es igualita a ti"


"Vos si no podes negar a tu hijo, es tu viva imágen"


Una clase (subclase) puede **heredar atributos y métodos** de otra (superclase).


Se establece con la palabra clave `extends`.


```java[]
class Persona {
    String nombre;
    public void saludar() {
        System.out.println("Hola, soy " + nombre);
    }
}

class Estudiante extends Persona {
    String carnet;
}
```

Aquí, `Estudiante` hereda `nombre` y `saludar()` de `Persona`.



## Jerarquía de clases


En Java, todas las clases heredan directa o indirectamente de `Object`.


Esto significa que cualquier objeto en Java tiene disponibles métodos como:

* `toString()` – representación en texto.
* `equals()` – comparación de igualdad.
* `getClass()` – obtener el tipo en tiempo de ejecución.


Ejemplo: `Object → Persona → Estudiante`.


Proposito:

* Organizar las clases en **niveles lógicos**.
* Permitir que las clases compartan **atributos y comportamientos comunes**.
* Facilitar el **polimorfismo**, al tratar objetos diferentes bajo un mismo tipo general.



## Acceso a miembros heredados


Una subclase **hereda** los miembros `public` y `protected`.


Los miembros `private` **no son heredados**, pero sí accesibles a través de getters/setters.


```java[]
class Padre {
    private int secreto;
    protected int protegido;
    public int publico;
}

class Hijo extends Padre {
    public void mostrar() {
        // secreto; // no accesible
        System.out.println(protegido); // accesible
        System.out.println(publico);   // accesible
    }
}
```



## Override


La **sobrescritura de métodos** ocurre cuando una subclase redefine el comportamiento de un método heredado de la superclase.


El método mantinen la **misma firma** (nombre, parámetros y tipo de retorno compatible).


Se utiliza para **personalizar o especializar** el comportamiento heredado.


La anotación `@Override` no es obligatoria, pero ayuda al compilador a detectar errores.


La resolución del método ocurre en **tiempo de ejecución** (polimorfismo dinámico).


No se pueden sobrescribir métodos `final`, `static` o `private`.


```java[]
class Persona {
    public void saludar() {
        System.out.println("Hola");
    }
}

class Estudiante extends Persona {
    @Override
    public void saludar() {
        System.out.println("Hola, soy estudiante");
    }
}
```



## Super


La palabra clave **`super`** se utiliza en herencia para referirse explícitamente a la superclase.


Permite invocar al **constructor de la superclase** desde la subclase.


Permite acceder a **métodos o atributos** de la superclase que han sido sobrescritos o están ocultos.


Útil para extender comportamientos heredados sin perder la lógica original.


```java[]
class Persona {
    public void saludar() {
        System.out.println("Hola");
    }
}

class Estudiante extends Persona {
    @Override
    public void saludar() {
        super.saludar(); // invoca método de superclase
        System.out.println("... y también estudiante");
    }
}

class Profesor extends Persona {
    public Profesor() {
        super(); // invoca al constructor de Persona
    }
}
```



## Polimorfismo


El **polimorfismo** es la capacidad de un objeto de adoptar múltiples formas.


Esto permite que el mismo método tenga diferentes comportamientos según el tipo real del objeto en tiempo de ejecución.


Una referencia de la **superclase** puede apuntar a un objeto de cualquier **subclase**.


Permite escribir código más **genérico y extensible**, trabajando con la superclase pero obteniendo el comportamiento de la subclase.


```java[]
class Persona {
    public void saludar() {
        System.out.println("Hola");
    }
}

class Estudiante extends Persona {
    @Override
    public void saludar() {
        System.out.println("Hola, soy estudiante");
    }
}

class Profesor extends Persona {
    @Override
    public void saludar() {
        System.out.println("Buenos días, soy profesor");
    }
}

public class Main {
    public static void main(String[] args) {
        Persona p1 = new Estudiante();
        Persona p2 = new Profesor();

        p1.saludar(); // Hola, soy estudiante
        p2.saludar(); // Buenos días, soy profesor
    }
}
```



## Upcasting y Downcasting


```java[]
Persona p = new Estudiante(); // upcasting implícito

Estudiante e = (Estudiante) p; // downcasting explícito
```


* **Upcasting:** seguro, siempre válido.
* **Downcasting:** puede lanzar `ClassCastException` si la referencia no es del tipo esperado.



## Arreglos y polimorfismo


Una de las ventajas del polimorfismo es poder trabajar con colecciones de la superclase y almacenar objetos de distintas subclases. Esto facilita el manejo uniforme de diferentes tipos de objetos.


```java[]
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Persona> personas = new ArrayList<>();
        
        personas.add(new Estudiante());
        personas.add(new Profesor());
        personas.add(new Estudiante());

        for (Persona p : personas) {
            // Cada objeto ejecuta su propia versión
            p.saludar();
        }
    }
}
```


Solo un `ArrayList<Persona>` maneja objetos de diferentes subclases gracias al polimorfismo.



## Clases abstractas y herencia


Una clase abstracta **no puede instanciarse**.


Puede contener métodos abstractos (sin implementación).


Las subclases deben implementar los métodos abstractos.


Es una especie de contato. Yo (subclase) me comprometo a implementar los métodos que se definen en la clase abastracta.


```java[]
abstract class Animal {
    public abstract void hacerSonido();
}

class Perro extends Animal {
    @Override
    public void hacerSonido() {
        System.out.println("Guau");
    }
}
```



## Final


`final class` → no puede ser extendida.


`final` en un método → no puede ser sobreescrito.


```java[]
final class Constante {
    // no se puede extender
}

class Base {
    public final void metodo() {}
}

class Derivada extends Base {
    // @Override metodo() ❌ error
}
```



## Buenas prácticas


Usen herencia solo si existe relación **is-a**.


Prefieran **composición** si es un caso “tiene-un”.


Eviten jerarquías profundas y complejas.


Documenten las clases base para que sea claro qué debe heredarse.



## Limitaciones


No hay herencia múltiple de clases en Java.


Puede generar acoplamiento excesivo.


Difícil de mantener en jerarquías muy profundas.


**Alternativa:** interfaces y composición.
