# Vistas de la app (Views)

En Codoozer, se llama vista (view) a lo que sería una pantalla de la app. Puede haber tantas vistas como se quiera. Cada una se define en un archivo JSON independiente, que debe estar alojado en la carpeta `views`.


La siguiente tabla muestra los parámetros que puede contener:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | id | Obligatorio | Identificador único de la vista |
  | title | Opcional | Nombre de la vista. Si la vista está incluida en un contenedor con ActionBar, el título se mostrará en dicha barra. |
  | [view_wrapper](#contenedor-de-una-vista-view_wrapper) | Obligatorio | ID del contenedor de vista a utilizar. |
  | [events](#eventos-de-la-vista) | Opcional | Define el comportamiento de la vista como respuesta a determinados eventos.|
  | [content](#contenido-de-la-vista) | Obligatorio | Define el contenido de la vista |
  


Si quieres ver un emplo de archivo json para una vista, [pincha aquí](view.json)




## Contenedor de una vista (view_wrapper)
El parámetro `view_wrapper` indica el tipo de contenedor que va a utilizar esta vista, de entre los definidos en la carpeta `view_wrappers`.

Para más información sobre los view_wrappers, [pincha aquí](../view_wrappers)




## Eventos de la vista
El parámetro `events` contiene un objeto JSON que incluye la lista de eventos para los cuales queremos que la app reaccione cuando está cargada una vista concreta.

Estos son los eventos disponibles:

  | Key  | Descripción |
  | ------------- | ------------- |
  | onbackpressed | Se produce cuando el usuario pulsa la tecla de volver o se ejecuta alguna función `back`. En caso de añadirse este evento, se bloquea el comportamiento de volver atrás. Será necesario incluir una función `back` al final de la secuencia si se desea volver a la view anterior al terminar la ejecución de las funciones añadidas en este evento. |
  | onexit | Se produce justo antes abandonar la vista. |
  | onloaded | Se produce una vez la vista ha sido cargado |
  | onpreload | Se produce justo antes de cargarse la vista. En caso de ejecutarse algunos tipos de funciones, como la función `goto`, se podría interrumpir la carga de la vista actual.  |
  | onreturned | Se produce cuando se vuelve a esta view tras haber visitado otra view. |

Aquí se puede ver un ejemplo:

<pre>
    "events":{
        "onpreload": {"function":"goto","what":"@property.score","value":"main"}
    },
</pre>


## Contenido de la vista
El parámetro `content` contiene un array JSON que contiene la lista de componentes visuales que queremos incluir en la vista.

Los componentes que se pueden incluir son:

| Key  | Descripción |
| ------------- | ------------- |
| banner | Banner de publicidad |
| button | Botón |
| [cropper](components/cropper) | Imagen |
| group | Grupo que permite incluir dentro otros componentes |
| [image](components/image) | Imagen |
| [inputtext](components/inputtext) | Campo de entrada de texto |
| [list](components/list) | Lista o rejilla |
| [map](components/map) | Mapa de GoogleMaps |
| pdfviewer | Visor de archivos pdf |
| [range](components/range) | Selector con barra de desplazamiento |
| [scanner](components/scanner) | Escáner de códigos de barra y QR |
| [stripe_checkout](components/stripe_checkout) | Muestra una página de checkout para pagos mediante Stripe |
| [switch](components/switch) | Conmutador on/off |
| text | Para mostrar un texto |
| [video](components/video) | Vídeo |
| web | Para mostrar una página web incrustada |

Todos los componentes se definen como objetos JSON, los cuales contendrán unos parámetros generales, independientes del tipo de componente de que se trate, así como otros parámetros específicos en función del tipo de componente.

Los parámetros comunes son:

  | Key  | Caracter | Valor por defecto | Descripción |
  | ------------- | ------------- | ------------- | ------------- |
  | [background](#background) | Opcional | | Define el fondo del componente. El valor es un objeto JSON en el que se define el fondo. |
  | events | Opcional || Define si hay que lanzar alguna función como respuesta a algún evento. Los tipos de eventos pueden variar en función del tipo de componente, aunque el evento `onclick` será común a todos los tipos de componente, aunque podría haber alguna excepción.|
  | halign | Opcional | center | Alineamiento horizontal del componente con respecto a su contenedor. Puede ser `start`, `left`, `center`, `right` o `end`. |
  | height | Opcional | fill | Alto del elemento. Puede tener los valores `fill`, `wrap`, un número de puntos de densidad (dp), o un porcentaje. |
  | [if](#condicionales) | Opcional || Permite definir una condición, de modo que el componente solo se muestre en caso de cumplirse dicha condición. El valor es un objeto JSON.|
  | [margin](#márgenes-y-padding) | Opcional | 0 | Define los márgenes que hay que dejar alrededor del componente, con respecto a los límites del contenedor o a los límites de componentes adyacentes.|
  | [padding](#márgenes-y-padding) | Opcional | 0 | Define los márgenes internos que hay que dejar entre los límites del componente y su contenido.|
  | valign | Opcional | middle | Alineamiento vertical del componente con respecto a su contenedor. Puede ser `top`, `middle` o `bottom`.|
  | width | Opcional | fill | Ancho del elemento. Puede tener los valores `fill`, `wrap`, un número de puntos de densidad (dp), o un porcentaje. |
  | visible | Opcional | true | Indica si un componente debe mostrarse en pantalla o no. |
  
  
## Background
El fondo de un objeto se define mediante un objeto JSON que debe tener estos parámetros:

| Key  | Descripción |
| ------------- | ------------- |
| type | Tipo de fondo. Puede ser `solid` o `image`. |
| color | En caso de ser un fondo de tipo `solid`, el valor sería o un color (formato #RRGGBB o #AARRGGBB) o una referencia a un color de la tabla de colores (p.ej.: @color.white). |
| image | En caso de un fondo de tipo `image`, habría que indicar el nombre del archivo que contiene la imagen. |

## Condicionales
Los condicionales se utilizan para especificar si la aparición de un componente debe ocurrir solo en caso de que se cumpla cierta condición. Los condicionales se definen mediante el parámetro `if`, cuyo valor será un objeto JSON, que podrá tener a su vez estos parámetros:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | what | Obligatorio | Referencia que queremos evaluar |
  | is | Opcional | Valor o referencia con cuyo valor queremos comparar. La condición se cumplirá si el valor de `what` es igual al valor especificado en `is`.|
  | is_not | Opcional | Valor o referencia con cuyo valor queremos comparar. La condición se cumplirá si el valor de `what` es distinta al valor especificado en `is_not`.|
  | less_than | Opcional | Valor o referencia con cuyo valor queremos comparar. La condición se cumplirá si el valor de `what` es menor al especificado en `less_than`.|
  | more_than | Opcional | Valor o referencia con cuyo valor queremos comparar. La condición se cumplirá si el valor de `what` es mayor al especificado en `less_than`.|
  
  

## Márgenes y padding
Tanto el parámetro `margin` como el de `padding` puede tener un valor numérico (como puntos de densidad), para definir el margen o padding en las 4 direcciones, o un objeto JSON si se quiere especificar un valor en una o varias de las direcciones (top, start, bottom, end).

<pre>
  "margin":40,
  "padding":{
    "top":10,
    "bottom":10
  }
