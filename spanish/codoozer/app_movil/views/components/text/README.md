# Componente TEXT

El componente `text` muestra un texto.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | color | Opcional | Color del texto. | 
  | decimals | Opcional | Limita el número de decimales a mostrar si el texto es un número que procede de una referencia establecida en el parámetro `source`. | 
  | field | Opcional | En caso de encontrarse el componente dentro de un componente de tipo `list`, este parámetro indicará el campo del origen de datos (p.ej. una colección de una base de datos) que contendría la ruta al archivo.|
  | font | Opcional | Es la tipografía a utilizar.|
  | font_size | Opcional | Tamaño del texto. |
  | text | Opcional | Texto a incluir por defecto en la caja de texto.|
  | text_align | Opcional | Alineamiento horizontal del texto dentro de la caja. Puede tener los valores `start`,`center` o `end`.|
  | text_valign | Opcional | Alineamiento vertical del texto dentro de la caja. Puede tener los valores `top`,`middle` o `bottom`.|
  | selectable | Opcional | Indica si queremos permitir al usuario seleccionar el texto, o parte de él, tras mantener el dedo pulsando el texto. Por defecto, si no existe el parámetro, el valor será `false`,|
  | source | Opcional | Indica de qué referencia (una property, una cookie, etc.) debe obtenerse el texto. |
  


## Eventos

El componente `text` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
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
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |
