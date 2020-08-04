# Componente SELECT

El componente `select` es un componente que permite al usuario seleccionar un valor de entre una lista de valores desplegable.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | border | Opcional | Color del borde del componente. El valor puede ser un color en formato #AARRGGB, un color en formato #RRGGBB, o una referencia a un color de la tabla de colores. También podría tener como valor un objeto JSON, en el cual se podrían especificar de forma independiente los colores de los bordes `top`, `bottom`, `start` y `end`.  |
  | color | Opcional | Color principal del texto y de la flecha del desplegable. Si no se especifica, se utilizará el color @color.accent |
  | dropdown_background | Opcional | Color de fondo del desplegable.|
  | dropdown_color | Opcional | Color del texto del desplegable. Si no se especifica, se utilizará el especificado en el parámetro `color`, si existe.| 
  | dropdown_font | Opcional | Tipografía a utilizar en el desplegable. Si no se especifica, se utilizará el especificado en el parámetro `font`, si existe.|
  | dropdown_font_size | Opcional | Tamaño de fuente en el desplegable. Si no se especifica, se utilizará el especificado en el parámetro `font_size`, si existe.| 
  | dropdown_padding | Opcional | Es un valor numérico que indica el margen interior en las opciones del desplegable, medido en dpi.| 
  | font | Opcional | Es la tipografía a utilizar.|
  | font_size | Opcional | Tamaño del texto. |
  | mode | Opcional | Indica el tipo de desplegable a utilizar. Puede ser `dropdown` o `dialog`. Con el primero, la lista se desplegará en la posición donde está el componente. Con el segundo, la lista flotará en la pantalla en una zona determinada, independientemente de la posición del componente. Por defecto, si no se especifica, será `dropdown`.|
  | [options](#opciones) | Obligatorio | La lista de opciones de entre las cuales se elegirá el valor del componente.|
  | [onchanged](#eventos) | Opcional | Evento que se producte cuando el usuario cambia la selección..|
  | source | Opcional | Indica con qué referencia (una property, una cookie, etc.) debe sincronizarse el contenido del selector. Es decir, dónde se tiene que almacenar el texto que escriba el usuario y cuál debe ser el valor inicial de la caja de texto. |
  
Este componente no acepta background de tipo `image`, solo background de tipo `color`. De no especificarse, se utilizará el @color.primaryLight.

Hay que prestar atención a que este componente guardará en la referencia especificada en `source` el `value` de la opción seleccionada, no el `label`. De este modo, el valor de la selección será independiente del idioma de la app. Para poder usar el contenido de `label`, se puede utilizar la referencia `@element.[id_del_componente].label`.

## Opciones

La lista de opciones es un array de objetos JSON. Cada objeto tendrá estos parámetros:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | value | Obligatorio | Valor asociado a la opción. Es el valor que se guardará en la referencia indicada en `source`. |
  | label | Opcional | El texto a mostrar en la lista desplegable para la opción correspondiente. Puede aceptar multilenguaje. Si no se especifica, la lista mostrará el valor especificado en `value`. |

## Eventos

El componente `select` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onchanged | Se produce cuando el usuario cambia el valor seleccionado en el componente. Hay que tener en cuenta que este evento no se invocará si el componente cambia de valor por el hecho de que la referencia en el parámetro `source` haya cambiado de valor. |


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
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |
