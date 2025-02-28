# Prueba de WebSocket

[url socket](https://albert0gr.github.io/webSocket/)

Este repositorio contiene un ejemplo simple de uso de WebSocket utilizando SockJS y StompJS. El ejemplo muestra cómo conectarse a un servidor WebSocket, suscribirse a un tópico y mostrar los mensajes recibidos en una página web.

## Tecnologías utilizadas

- **HTML5** para la estructura del documento.
- **JavaScript** para la lógica de conexión y manejo de mensajes.
- [**SockJS-client**](https://cdnjs.cloudflare.com/ajax/libs/sockjs-client/1.6.1/sockjs.min.js) para la compatibilidad de WebSocket en distintos navegadores.
- [**StompJS**](https://cdnjs.cloudflare.com/ajax/libs/stomp.js/2.3.3/stomp.min.js) para la comunicación basada en el protocolo STOMP.

## Descripción

El archivo `index.html` implementa las siguientes funcionalidades:

- **Conexión al WebSocket:** Se conecta al endpoint `http://localhost:8080/ws` usando SockJS.
- **Configuración de STOMP:** Utiliza StompJS para establecer la comunicación sobre el WebSocket.
- **Suscripción a un tópico:** Se suscribe al tópico `/topic/reportes` para recibir mensajes enviados por el servidor.
- **Visualización de mensajes:** Muestra los mensajes recibidos en la página, actualizando dinámicamente la interfaz de usuario.

## Cómo utilizar

1. **Configuración del servidor WebSocket:**

   Asegúrate de tener un servidor WebSocket corriendo en `http://localhost:8080/ws` y que esté configurado para emitir mensajes en el tópico `/topic/reportes`.

2. **Ejecutar el ejemplo:**

   - Clona o descarga el repositorio.
   - Abre el archivo `index.html` en tu navegador.
   - La página mostrará un mensaje de "Conectando..." y, una vez establecida la conexión, se actualizará a "Conectado" junto con la información del frame de conexión.
   - Los mensajes enviados desde el servidor al tópico `/topic/reportes` se mostrarán en la sección de mensajes de la página.

## Personalización

Si necesitas modificar la URL del servidor WebSocket o el tópico de suscripción, edita las siguientes líneas en el código JavaScript dentro del archivo `index.html`:

```javascript
// Conecta al endpoint del WebSocket
var socket = new SockJS('http://localhost:8080/ws');
var stompClient = Stomp.over(socket);

// Suscribirse al tópico (modifica según sea necesario)
stompClient.subscribe('/topic/reportes', function(message) {
  // Procesa el mensaje recibido
});
