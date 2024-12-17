### Abstracción

El Polimorfismo permite tratar a las clases hijas como si fueran iguales que la clase base. Desde el punto de vista del porgrama las clases hijas se "comportan como" la clase base, pero ejecutan su propia versión de los métodos.

![Aplicación de Abtracción en la clase "Socio"]()
- [Diagrama de la clase]()

Aplicado al sistema: En el sistema del gimnasio, todos los socios tienen caracteristicas comunes(por ejemplo, nombre, email, etc.) y un metodo general como (AccesoGimnasio). La clase abstracta Socio define los atributos comunes y metodos que deben si o si implementarse. No se crean directamente un "Socio", sino que se crean subclases especificas como "SocioRegular" o "SocioPremium".

```java
// Clase abstracta Socio
public abstract class Socio {
    private String nombre;
    private String dni;

    // Constructor
    public Socio(String nombre, String dni) {
        this.nombre = nombre;
        this.dni = dni;
    }

    // Métodos para obtener los atributos
    public String getNombre() {
        return nombre;
    }

    public String getDni() {
        return dni;
    }

    // Método abstracto: obliga a las subclases a implementarlo
    public abstract void accesoAlGimnasio();
}

public class SocioRegular extends Socio {
    // Constructor
    public SocioRegular(String nombre, String dni) {
        super(nombre, dni); // Llama al constructor de la clase base
    }

    // Implementación del método abstracto
    @Override
    public void accesoAlGimnasio() {
        System.out.println(getNombre() + " tiene acceso al gimnasio en horarios regulares.");
    }
}

public class SocioPremium extends Socio {
    // Constructor
    public SocioPremium(String nombre, String dni) {
        super(nombre, dni);
    }

    // Implementación del método abstracto
    @Override
    public void accesoAlGimnasio() {
        System.out.println(getNombre() + " tiene acceso al gimnasio en cualquier horario.");
    }
}

Ejemplo:

public class Gimnasio {
    public static void main(String[] args) {
        // Crear un socio regular
        Socio socioRegular = new SocioRegular("Ana", "12345678");

        // Crear un socio premium
        Socio socioPremium = new SocioPremium("Carlos", "87654321");

        // Llamar al método accesoAlGimnasio() en ambos
        socioRegular.accesoAlGimnasio(); // Ana tiene acceso al gimnasio en horarios regulares.
        socioPremium.accesoAlGimnasio(); // Carlos tiene acceso al gimnasio en cualquier horario.
    }
}

Salida:
Ana tiene acceso al gimnasio en horarios regulares.
Carlos tiene acceso al gimnasio en cualquier horario.

```