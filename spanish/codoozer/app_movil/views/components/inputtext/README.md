# Componente INPUTTEXT

El componente `inputtext` muestra un campo de texto donde el usuario puede escribir.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | border_color | Opcional | Color del borde de la caja de texto |
  | border_color_focus | Opcional | Color del borde de la caja en caso de que ésta tenga el foco. |
  | color | Opcional | Color del texto. | 
  | field | Opcional | En caso de encontrarse el componente dentro de un componente de tipo `list`, este parámetro indicará el campo del origen de datos (p.ej. una colección de una base de datos) que contendría la ruta al archivo.|
  | font | Opcional | Es la tipografía a utilizar.|
  | font_size | Opcional | Tamaño del texto. |
  | format | Opcional | Indica el tipo de texto que se va a escribir. Puede ser los valores `plain`, `email`, `number`, `decimal` o `password`, para forzar que el usuario tenga que escribir un texto plano, un email, un número entero, un número con decimales o una contraseña. En función del formato, cambiaría el tipo de teclado donde el usuario escribiría.|
  | hint | Opcional | Texto a mostrar dentro de la caja de texto, atenuado, cuando no contiene ningún texto. Se puede utilizar, por ejemplo, para indicar las instrucciones al usuario sobre lo que tiene que escribir.|
  | hint_color | Opcional | Color del texto hint. | 
  | text | Opcional | Texto a incluir por defecto en la caja de texto.|
  | text_align | Opcional | Alineamiento horizontal del texto dentro de la caja. Puede tener los valores `start`,`center` o `end`.|
  | text_valign | Opcional | Alineamiento vertical del texto dentro de la caja. Puede tener los valores `top`,`middle` o `bottom`.|
  | source | Opcional | Indica con qué referencia (una property, una cookie, etc.) debe sincronizarse el contenido de la caja de texto. Es decir, dónde se tiene que almacenar el texto que escriba el usuario y cuál debe ser el valor inicial de la caja de texto. |
  


## Eventos

El componente `inputtext` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onchanged | Se produce cuando el usuario cambia el contenido de la caja de texto. Es decir, cuando escribe o borra una letra. Hay que tener en cuenta que este evento no se invocará si el componente cambia de valor por el hecho de que la referencia en el parámetro `source` haya cambiado de valor. |
  | onclick | Se produce cuando el usuario toca el componente. |



## Referencias

Este componente permite acceder a ciertas propiedades a través de referencias, usando el siguiente formato:

```
@element.id_del_componente.propiedad
```

 | Propiedad | Modo | Descripción |
  | ------------- | ------------- | ------------- |
  | alpha | Escritura | Opacidad del componente, un valor entre 0 (0%) y 1 (100%) |
  | backgroundColor | Escritura | Color de fondo del componente. Acepta un color de la tabla de colores (@color.primary) o un valor hexadecimal en formato #AARRGGBB o #RRGGBB |
  | color | Escritura | Establece el color del texto |
  | font | Escritura | Establece la tipografía a usar en el texto como una referencia a la tabla `fonts` (@font.arial) |
  | font_size | Escritura | Establece el tamaño de letra |
  | hint_color | Escritura | Establece el color del hint (texto temporal que se muestra cuando el inputtext está vacío) |
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |

