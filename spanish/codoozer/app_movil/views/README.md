# Vistas de la app (Views)

En Codoozer, se llama vista (view) a lo que sería una pantalla de la app. Puede haber tantas vistas como se quiera. Cada una se define en un archivo JSON independiente, que debe estar alojado en la carpeta `views`.


La siguiente tabla muestra los parámetros que puede contener:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | id | Obligatorio | Identificador único de la vista |
  | title | Opcional | Nombre de la vista. Si la vista está incluida en un contenedor con ActionBar, el título se mostrará en dicha barra. |
  | [view_wrapper](#contenedor-de-una-vista-view_wrapper) | Obligatorio | ID del contenedor de vista a utilizar. |
  | [events](#eventos-de-la-vista) | Opcional | Define el comportamiento de la vista como respuesta a determinados eventos.|
  | content | Obligatorio | Define el contenido de la vista |
  


Si quieres ver un emplo de archivo json para una vista, [pincha aquí](view.json)




## Contenedor de una vista (view_wrapper)
El parámetro `view_wrapper` indica el tipo de contenedor que va a utilizar esta vista, de entre los definidos en la carpeta `view_wrappers`.

Para más información sobre los view_wrappers, [pincha aquí](../view_wrappers)




## Eventos de la vista
El parámetro `events` contiene un objeto JSON que incluye la lista de eventos para los cuales queremos que la app reaccione cuando está cargada una vista concreta..

Estos son los eventos disponibles:

  | Key  | Descripción |
  | ------------- | ------------- |
  | onloaded | Se produce una vez la vista ha sido cargado |
  | onpreload | Se produce justo antes de cargarse la vista. En caso de ejecutarse algunos tipos de funciones, como la función `goto`, se podría interrumpir la carga de la vista actual.  |


Aquí se puede ver un ejemplo:

<pre>
    "events":{
        "onpreload": {"function":"goto","what":"@property.score","value":"main"}
    },
</pre>

