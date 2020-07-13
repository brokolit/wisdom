# Componente SWITCH

El componente `switch` es un tipo de selector que permite al usuario elegir entre dos valores: verdadero o falso (`true` o `false`). Tiene forma de pequeño interruptor.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | color_off | Opcional | Indica el color del componente cuando está desactivado. Puede ser un color de la tabla (p.ej: @color.primary) o un color hexadecimal en formato #RRGGBB o #AARRGGBB.|
  | color_on | Opcional | Indica el color del componente cuando está activado. Puede ser un color de la tabla (p.ej: @color.primary) o un color hexadecimal en formato #RRGGBB o #AARRGGBB.|
  | field | Opcional | En caso de que el componente esté dentro de una lista, el parámetro field indica el campo de la colección asociada a la lista que contendrá el valor inicial del componente. |
  | source | Opcional | Si queremos vincular el valor del selector a una referencia, de modo que cuando el usuario cambie el interruptor, se actualice el valor de dicha referencia. O, por el contrario, si se cambia el valor de la referencia, que se actualice la posición del cursor en el componente. |
  


## Eventos

El componente `range` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onchanged | Se produce cuando el usuario cambia el valor del interruptor. Hay que tener en cuenta que este evento no se invocará si el componente cambia de valor por el hecho de que la referencia en el parámetro `source` haya cambiado de valor. |


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
  | value | Escritura | Permite establecer el valor del rango. |
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |
