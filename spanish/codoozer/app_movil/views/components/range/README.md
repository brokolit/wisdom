# Componente RANGE

El componente `range` es un tipo de selector que permite al usuario elegir un número dentro de un rango determinado. Muestra una barra horizontal, con un cursor que se puede deslizar a lo largo de la barra.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | field | Opcional | En caso de que el componente esté dentro de una lista, el parámetro field indica el campo de la colección asociada a la lista que contendrá el valor inicial del componente. |
  | min | Opcional | Es el valor mínimo del rango, que equivale a que el cursor esté totalmente al principio de la barra. De no incluir este parámetro, se considera que el valor mínimo es cero. |
  | max | Opcional | Es el valor máximo del rango, que equivale a que el cursor esté totalmente al final de la barra. De no incluir este parámetro, se considera que el valor máximo es 100. |
  | step | Opcional | Indica el incremento en el valor final por cada posición que se mueva el cursor hacia la derecha. Si no se especifica este parámetro, toma el valor 1. |
  | value | Opcional | Se utiliza para definir el valor inicial del selector `range`.|
  | source | Opcional | Si queremos vincular el valor del selector a una referencia, de modo que cuando el usuario cambie el cursor de posición, se actualice el valor de dicha referencia. O, por el contrario, si se cambia el valor de la referencia, que se actualice la posición del cursor en el componente. |
  


## Eventos

El componente `range` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onchanged | Se produce cuando el usuario mueve el cursor y el componente cambia de valor. Hay que tener en cuenta que este evento no se invocará si el componente cambia de valor por el hecho de que la referencia en el parámetro `source` haya cambiado de valor. |

