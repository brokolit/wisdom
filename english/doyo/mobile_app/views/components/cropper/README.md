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


 
## Referencias

El componente `image` permite acceder a ciertas propiedades a través de referencias, usando el siguiente formato:

```
@element.id_del_componente.propiedad
```

Las propiedades de escritura se podrán establecer como parámetro `what` de una función `set`.
Las propiedades de lectura se podrán usar como valor en aquellas funciones que acepten valores en forma de referencias.


 | Propiedad | Modo | Descripción |
  | ------------- | ------------- | ------------- |
  | alpha | Escritura | Opacidad del componente, un valor entre 0 (0%) y 1 (100%) |
  | backgroundColor | Escritura | Color de fondo del componente. Acepta un color de la tabla de colores (@color.primary) o un valor hexadecimal en formato #AARRGGBB o #RRGGBB |
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |
