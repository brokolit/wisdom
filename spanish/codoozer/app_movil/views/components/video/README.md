# Componente VIDEO

El componente `video` se encarga de mostrar una vídeo.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | autoplay | Opcional | Indica si el vídeo debe iniciar su reproducción de forma automática una vez esté listo para reproducirse. Puede ser `true` o `false`. Si no se especifica, se considera `true`.|
  | field | Opcional | En caso de encontrarse el componente dentro de un componente de tipo `list`, este parámetro indicará el campo del origen de datos (p.ej. una colección de una base de datos) que contendría la ruta al archivo.
  | file | Opcional | Es el archivo mp4 que contiene el vídeo.|
  | loop | Opcional | Indica si el vídeo debe reproducirse desde el principio cada vez que termine. Puede ser `true` o `false`. Si no se especifica, se considerará `false`.|
  | scale | Opcional | Especifica cómo se tiene que escalar el vídeo para adaptarse a los límites del componente. Actualmente puede contener el valor `crop`, que hará que el vídeo se escale para rellenar totalmente los límites del componente, pudiendo salirse de los límites horizontales o los verticales. Si no se especifica este parámetro, en caso de que la altura del componente no sea `wrap`, la imagen se estiraría para rellenar todo el área del componente.|
  | source | Opcional | Indica si el vídeo a mostrar debe obtenerse de alguna referencia.|
  


## Eventos

El componente `video` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onclick | Se produce cuando el usuario toca el componente. |
  | onfinished | Se produce cuando la reproducción del vídeo llega a su fin. |
  | onready | Se produce cuando archivo de vídeo se ha cargado y está listo. |


## Propiedades

Mediante una función `set`, se pueden editar estas propiedades del componente (@element.id):

  | Nombre  | Descripción |
  | ------------- | ------------- |
  | play | Puede ser `true` o `false`. Un valor `true` pondrá el vídeo en modo reproducción si estaba pausado. Un valor `false` pausará el vídeo si se estaba reproduciendo. |
  | position | Establece la posición, en segundos (acepta decimales), desde la que queremos que se reproduzca el vídeo. |


Por otro lado, podemos obtener las siguientes propiedades del componente. Por ejemplo, como `value` en una función `set`:

    | Nombre  | Descripción |
  | ------------- | ------------- |
  | duration | Es la duración total del vídeo, en segundos. |
  | play | Vale `true` si el vídeo se está reproduciendo o `false` si está pausado. |
  | position | Es la posición actual de la reproducción, en segundos. |
  


