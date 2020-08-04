# Componente LIST

El componente `list` muestra una lista de registros de una colección (base de datos local o Firebase) o las opciones de un menú definido en la carpeta `menus`.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | columns | Opcional | Si se quiere convertir la lista en una rejilla, se puede establecer el número de columnas. Si no se especifica, se considera que es una lista de una sola columna.|
  | content | Obligatorio | Contiene la plantilla de componentes que se repetirá en cada una de las filas y/o columnas de la lista. Algunos tipos de componente tienen el parámetro `field` que se utilizará para indicar que el contenido de dicho componente se obtendrá de la colección indicada en `data_source`, siendo el  campo especificado en el parámetro `field`. En el caso de que `data_source` sea un menú, se podrá utilizar el field `index` para mostrar el número de registro o subregistro.|
  | data_source | Obligatorio | Contiene la referencia a la colección o el menú del cual se obtendrán los datos.|
  
 

## Eventos

El componente `image` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onclick | Se produce cuando el usuario toca la imagen. |


 
## Referencias

Este componente permite acceder a ciertas propiedades a través de referencias, usando el siguiente formato:

```
@element.id_del_componente.propiedad
```

Las propiedades de escritura se podrán establecer como parámetro `what` de una función `set`.
Las propiedades de lectura se podrán usar como valor en aquellas funciones que acepten valores en forma de referencias.


 | Propiedad | Modo | Descripción |
  | ------------- | ------------- | ------------- |
  | alpha | Escritura | Opacidad del componente, un valor entre 0 (0%) y 1 (100%) |
  | backgroundColor | Escritura | Color de fondo del componente. Acepta un color de la tabla de colores (@color.primary) o un valor hexadecimal en formato #AARRGGBB o #RRGGBB |
  | selected | Lectura | Devuelve el ID o KEY del documento de la colección asociado a la última fila que se ha pulsado. En caso de que los documentos de la colección no tengan claves, devolverá el número de fila (empezando por el cero).|
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |
