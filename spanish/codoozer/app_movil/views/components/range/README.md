# Componente RANGE

El componente `range` es un tipo de selector que permite al usuario elegir un número dentro de un rango determinado. Muestra una barra horizontal, con un cursor que se puede deslizar a lo largo de la barra.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | start | Opcional | Es el valor mínimo del rango, que equivale a que el cursor esté totalmente al principio de la barra. De no incluir este parámetro, se considera que el valor mínimo es cero. |
  | steps | Opcional | Es el número de posiciones que puede ocupar el cursor a través de la barra horizontal. Si no se incluye este parámetro, el número de posiciones es 100. |
  | step | Opcional | Indica el incremento en el valor final por cada posición que se mueva el cursor hacia la derecha. Si no se especifica este parámetro, toma el valor 1. |
  | value | Opcional | Se utiliza para definir el valor inicial del selector `range`.|
  | source | Opcional | Si queremos vincular el valor del selector a una referencia, de modo que cuando el usuario cambie el cursor de posición, se actualice el valor de dicha referencia. O, por el contrario, si se cambia el valor de la referencia, que se actualice la posición del cursor en el componente. |
  


## Eventos

El componente `range` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onchanged | Se produce cuando el usuario mueve el cursor y el componente cambia de valor. Hay que tener en cuenta que este evento no se invocará si el componente cambia de valor por el hecho de que la referencia en el parámetro `source` haya cambiado de valor. |

