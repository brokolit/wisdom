# Componente MAP

El componente `map` muestra un mapa online en el área definida.


La siguiente tabla muestra los parámetros que puede contener, más allá de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | buildings | Opcional | Determina si se quiere mostrar edificios en el mapa. Puede tener los valores `true` o `false`. Si no se especifica el parámetro, se considera valor `false`. |
  | center | Opcional | Es la posición inicial sobre la que se debe centrar el mapa. Puede ser una cadena de texto en formato "latitud,longitud", o una referencia que contenga dicha ubicación. En caso de usarse una referencia, el mapa se irá centrando cada vez que el valor de la variable referida cambie. |
  | compass | Opcional | Determina si se quiere mostrar la brújula en el mapa. Puede tener los valores `true` o `false`. Si no se especifica el parámetro, se considera valor `false`. |
  | data_source | Opcional | Define un origen de datos que contiene los elementos a representar sobre el mapa (marcadores, formas, etc.) |
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
  | zoom | Nivel de zoom actual del mapa. |
