## Anexo - Aplicación de Patrón de Diseño 
El patron state es un patron de diseño de comportamiento que permite a un objeto alterar su comportamiento cuando su estado interno cambia.
Sin un mecanismo para manejar estos estado el codigo para gestionar las reservas podria volverse complejo y redundante.

#### Motivación
Las reservas de clases pueden tener diferentes estado (pendiente, confirmada, cancelada). 
Cada estado tiene un comportamiento asociado y el patrón Stateayuda a organizar y gestionar las diferentes logicas de comportamiento segun el estado de la reserva

#### Estructura de Clases
No se requiere mayores cambios ni nuevas clases para implementar este cambio, se utiliza la clase ya existente "ReservaClase" y se agrega la porpiedad de estado para representar el estado de la reserva. Y se agregar los metodos de confirmarReserva() y cancelarReserva() para que den valor a la propiedad "estado"

#### Ejemplo de Código
![Ejemplo de Código](./img/Captura%20de%20pantalla%202024-11-29%20222952.png)
