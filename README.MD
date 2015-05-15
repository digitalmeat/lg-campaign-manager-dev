# LG Campaign manager

## Código:

Llamados para desarrolladores:

### lg_form_resize

Obtiene el tamaño de la página interior del iframe.

### lg_form_done

Obtiene el fin del flujo del formulario del registro

```javascript
$(function(){
   $(document).ready(function(){
        // Create IE + others compatible event handler
        var eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
        var eventer = window[eventMethod];
        var messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";
        // Listen to message from child window
        eventer(messageEvent,function(e) {
          console.log( e.data )
          var type = e.data.type;
          switch(e.data.type) {
            case 'lg_form_resize':
              $('iframe#register').height( e.data.value )
              break;
            case 'lg_form_done':
              alert("Gracias por registrarte")
              break;
            default:
              // Nothing
          }
      },false);
   });
});
```

# Estilos de formulario

Los códigos para re-diseñar el formulario de registro están adjuntos en este repositorio. [Hoja de estilos acá](https://github.com/digitalmeat/lg-campaign-manager-dev/blob/master/form.css)

Al crear una campaña podrás escontrar una caja para poner los estilos, debes editarlos directamente ahí.