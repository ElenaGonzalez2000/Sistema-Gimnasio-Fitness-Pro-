## Anexo - Aplicación de Patrón de Diseño State
El patron state es un patron de diseño de comportamiento que permite a un objeto alterar su comportamiento cuando su estado interno cambia.
Sin un mecanismo para manejar estos estado el codigo para gestionar las reservas podria volverse complejo y redundante.

#### Motivación
Las reservas de clases pueden tener diferentes estado (pendiente, confirmada, cancelada). 
Cada estado tiene un comportamiento asociado y el patrón Stateayuda a organizar y gestionar las diferentes logicas de comportamiento segun el estado de la reserva

#### Estructura de Clases
No se requiere mayores cambios ni nuevas clases para implementar este cambio, se utiliza la clase ya existente "ReservaClase" y se agrega la porpiedad de estado para representar el estado de la reserva. Y se agregar los metodos de confirmarReserva() y cancelarReserva() para que den valor a la propiedad "estado"

#### Ejemplo de Código
```javascript
const ESTADOS_RESERVA = {
    CONFIRMADA: "confirmada",
    PENDIENTE: "pendiente",
    CANCELADA: "cancelada"
};

class ReservaClase {
    constructor(socio, clase) {
        this.socio = socio;
        this.clase = clase;
        this.estado = ESTADOS_RESERVA.PENDIENTE; // Estado por defecto
    }

    confirmarReserva() {
        if (this.estado === ESTADOS_RESERVA.PENDIENTE) {
            this.estado = ESTADOS_RESERVA.CONFIRMADA;
            console.log(`Reserva confirmada para ${this.socio.nombre} en la clase ${this.clase.getNombre()}`);
        } else {
            console.log(`No se puede confirmar la reserva. Estado actual: ${this.estado}`);
        }
    }

    cancelarReserva() {
        if (this.estado !== ESTADOS_RESERVA.CANCELADA) {
            this.estado = ESTADOS_RESERVA.CANCELADA;
            console.log(`Reserva cancelada para ${this.socio.nombre} en la clase ${this.clase.getNombre()}`);
        } else {
            console.log("La reserva ya está cancelada.");
        }
    }
}

// Ejemplo simulado:
const spinning = new clase("Spinning", "27/12/2024 09:00 AM", "Profesor : Laura Martinez", 20); // Creamos una nueva clase
const ana = new Socio("Ana"); //Creamos un usuario
const reservaAna = new ReservaClase(ana, spinning); // Creamos una reserva de la clase

reservaAna.confirmarReserva(); // Resultado obtenido: Reserva confirmada para Ana en la clase Spinning

reservaAna.cancelarReserva(); // Resultado obtenido: Reserva cancelada para Ana en la clase Spinning
reservaAna.cancelarReserva(); // Resultado: La reserva ya está cancelada.
```
