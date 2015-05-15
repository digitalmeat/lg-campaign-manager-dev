# LG Campaign manager

## Introducción

El formulario puede ser llamado de 2 formas posibles: via iframe o via link directo. Además este provee 2 eventos a utilizar para utilización de los desarrolladores que deseen implementar estos formularios. Ambos utilizan la api de postMessage() (https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage).

Adicionalmente, se provee el CSS pertinente al formulario para adaptar al sitio que lo contiene.


## Eventos JS

### lg_form_resize

Reporta cambios del alto del iframe, en caso de necesitar ajustar el contenedor para que el formulario se visualice sin scroll.

### lg_form_done

Reporta un envío exitoso del formulario, en caso de necesitar un cambio de página o mensaje al finalizar el flujo de este.

### Ejemplo de implementación de eventos(cross-browser)

```javascript
  
  // Crear un listener
  var eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
  var eventer = window[eventMethod];
  var messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";
  
  // Escuchar el evento
  eventer(messageEvent,function(e) {
    
    // Diferenciar entre los distintos eventos
    var type = e.data.type;
    switch(e.data.type) {
      case 'lg_form_resize':
        alert( e.data.value )
        break;
      case 'lg_form_done':
        alert("Registro terminado")
        break;
    }

},false);

```

## Estilos de formulario

Los códigos para re-diseñar el formulario de registro están adjuntos en este repositorio. [Hoja de estilos acá](https://github.com/digitalmeat/lg-campaign-manager-dev/blob/master/form.css)

Debes enviar el CSS resultante a la persona que te envió el código iframe.