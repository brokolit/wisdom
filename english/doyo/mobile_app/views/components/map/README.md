# Componente MAP

El componente `map` muestra un mapa online en el área definida.


La siguiente tabla muestra los parámetros que puede contener, más allá de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | buildings | Opcional | Determina si se quiere mostrar edificios en el mapa. Puede tener los valores `true` o `false`. Si no se especifica el parámetro, se considera valor `false`. |
  | center | Opcional | Es la posición inicial sobre la que se debe centrar el mapa. Puede ser una cadena de texto en formato "latitud,longitud", o una referencia que contenga dicha ubicación. En caso de usarse una referencia, el mapa se irá centrando cada vez que el valor de la variable referida cambie. |
  | compass | Opcional | Determina si se quiere mostrar la brújula en el mapa. Puede tener los valores `true` o `false`. Si no se especifica el parámetro, se considera valor `false`. |
  | [data_source](#data-source) | Opcional | Define un origen de datos que contiene los elementos a representar sobre el mapa (marcadores, formas, etc.) |
  | enable_location | Opcional | Establece si el mapa debe mostrar el botón para desplazarse hasta la ubicación actual del dispositivo. Puede valer `true` o `false`. Si no se especifica el parámetro, se considera el valor `false`. |
  | max_zoom | Opcional | Se utiliza para limitar el máximo nivel de zoom que queremos permitir al usuario, es decir, cuánto se podrá acercar como máximo el punto de vista al mapa. |
  | min_zoom | Opcional | Se utiliza para limitar el mínimo nivel de zoom que queremos permitir al usuario. No podrá alejar el punto de vista más allá de lo que establezca el zoom mínimo. |
  | rotation | Opcional | Determina si se quiere permitir al usuario rotar el mapa. Puede tener los valores `true` o `false`. Si no se especifica el parámetro, se considera valor `true`. |
  | tilt | Opcional | Determina si se quiere permitir al usuario inclinar el mapa y dotarlo de perspectiva. Puede tener los valores `true` o `false`. Si no se especifica el parámetro, se considera valor `false`. |
  | traffic | Opcional | Determina si se quiere mostrar el estado del tráfico en el mapa. Puede tener los valores `true` o `false`. Si no se especifica el parámetro, se considera valor `false`. |
  | type | Opcional | Indica el tipo de mapa a representar. Puede tener los valores: `normal`, `hybrid`, `satelite` o `terrain`. Dicho valor puede obtenerse a partir de una referencia. Si no se especifica, el valor por defecto es `normal`. |
  | zoom | Opcional | Es el zoom inicial que debe tener el mapa. Puede ser un valor numérico, o una referencia que contenga dicha valor. En caso de usarse una referencia, el mapa irá modificando su nivel de zoom cada vez que el valor de la variable referida cambie. Un valor de 4, es una visión muy alejada del mapa, mientras que un valor de 20, corresponde a un nivel de acercamiento alto. |
  


## Eventos

El componente `range` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onchanged | Se produce cuando el usuario hace scroll en el mapa. Es decir, se desplaza a través del mapa. El evento se dispara al terminar el desplazamiento. Hay que tener en cuenta que este evento no se invocará si la posición del mapa cambia por el hecho de que la referencia en el parámetro `center` haya cambiado de valor. |
  | onclick | Se produce cuando el usuario mueve el cursor y el componente cambia de valor. Hay que tener en cuenta que este evento no se invocará si el componente cambia de valor por el hecho de que la referencia en el parámetro `source` haya cambiado de valor. |
  | onready | Se produce cuando el mapa se ha cargado con éxito y está listo para ser utilizado. |
  
  
  ## Propiedades

Se pueden obtener algunas propiedades del mapa, a través de la referencia `@element` seguida de un punto y el ID del mapa.

Por ejemplo, si un componente MAP tiene el ID `mainMap`, podríamos acceder a la posición actual mediante la referencia:

> @element.mainMap.position


La siguiente tabla muestra las propiedades que se pueden obtener de un mapa, en modo lectura:


 | Propiedad  | Descripción |
  | ------------- | ------------- |
  | clickedLat | Latitud del último punto del mapa que el usuario haya tocado. |
  | clickedLng | Longitud del último punto del mapa que el usuario haya tocado. |
  | position | Coordenadas del punto central actual del mapa, en formato `latitud,longitud`. |
  | visible | Indica si el componente es visible (`true`) o no (`false`) |
  | zoom | Nivel de zoom actual del mapa. |
  
La siguiente tabla muestra las propiedades que se pueden obtener de un mapa, en modo escritura:

 | Propiedad  | Descripción |
  | alpha | Opacidad del componente, un valor entre 0 (0%) y 1 (100%) |
  | backgroundColor | Color de fondo del componente. Acepta un color de la tabla de colores (@color.primary) o un valor hexadecimal en formato #AARRGGBB o #RRGGBB |
  | visible | Indica si el componente es visible (`true`) o no (`false`) |



## data-source

El campo data-source debe contener una referencia a una colección, ya sea de una base de datos local o una base de datos de firebase. Dicha colección contendrá los elementos que deben representarse en el mapa: marcadores, círculos o imágenes.

El mapa estará escuchando a dicha colección continuamente y, en caso de que algún documento cambie o se añada uno nuevo, se actualizará el mapa.

Cada documento de la colección deberá contener estos parámetros:


 | Propiedad  | Descripción |
  | ------------- | ------------- |
  | type | Tipo de elemento. Debe ser `marker` o `circle`. |
  | lat | Latitud donde debe dibujarse el elemento. |
  | lng | Longitud donde debe dibujarse el elemento. |


Además, en función del tipo de elemento, se podrán usar estos otros parámetros.


Para elementos de tipo `marker`:

 | Propiedad  | Descripción |
  | ------------- | ------------- |
  | anchor_h | Valor entre 0 y 1 que indica el desplazamiento horizontal del icono con respecto al punto en el mapa. |
  | anchor_v | Valor entre 0 y 1 que indica el desplazamiento vertical del icono con respecto al punto en el mapa. |
  | icon | Ruta a una imagen que debe estar en la carpeta `res/assets`. |
  | rotation | Ángulo de rotación de la imagen, en grados. |



Para elementos de tipo `circle`:

 | Propiedad  | Descripción |
  | ------------- | ------------- |
  | color | Color de la superficie del círculo, pudiendo ser un color de la tabla de colores o un valor #RGB/#ARGB. |
  | radius | Radio en metros del círculo. |
  | stroke_color | Color del perímetro, pudiendo ser un color de la tabla de colores o un valor #RGB/#ARGB. |
  | stroke_width | Grosor del perímetro. |



