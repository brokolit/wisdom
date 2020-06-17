# Componente IMAGE

El componente `image` se encarga de mostrar una imagen.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | field | Opcional | En caso de encontrarse el componente dentro de un componente de tipo `list`, este parámetro indicará el campo del origen de datos (p.ej. una colección de una base de datos) que contendría la ruta al archivo.
  | file | Opcional | Es el archivo que contiene la imagen.|
  | scale | Opcional | Especifica cómo se tiene que escalar la imagen para adaptarse a los límites del componente. Actualmente puede contener el valor `crop`, que hará que la imagen se escale para rellenar totalmente los límites del componente, pudiendo salirse de los límites horizontales o los verticales. Si no se especifica este parámetro, en caso de que la altura del componente no sea `wrap`, la imagen se estiraría para rellenar todo el área del componente.|
  | source | Opcional | Indica si la imagen a mostrar debe obtenerse de alguna referencia.|
  


## Eventos

El componente `image` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onclick | Se produce cuando el usuario toca la imagen. |

