# LG Campaign manager

Llamados para desarrolladores:

### lg_form_resize

Obtiene el tamaño de la página interior del iframe.

### lg_form_done

Obtiene el fin del flujo del formulario del registro


## Código:

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