# Componente SCANNER

El componente `scanner` muestra un lector de códigos de barra y QR basado en la cámara del dispositivo.

Este componente necesita que se configure Firebase, pues utiliza la librería de Machine Learning que ofrece Firebase.


La siguiente tabla muestra los parámetros que puede contener, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | format | Opcional | Indica qué formato o formatos de códigos de barra se deben detectar. Si no se especifica, se detectarán todos los formatos, aunque la velocidad de escaneado podría decaer. El valor de este parámetro es una lista donde habrá que añadir todos los formatos deseados.|
  
 

## Eventos

El componente `image` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onchanged | Se produce cada vez que el escáner detecte un código de barras distinto al último leído. En caso de que el usuario toque el componente, se olvidará el último código detectado, con lo que el evento `onchanged` volvería a producirse si se vuelve a detectar el mismo código. |


 
## Referencias

El componente `scanner` permite acceder a ciertas propiedades a través de referencias, usando el siguiente formato:

```
@element.id_del_componente.propiedad
```

Las propiedades de escritura se podrán establecer como parámetro `what` de una función `set`.
Las propiedades de lectura se podrán usar como valor en aquellas funciones que acepten valores en forma de referencias.


 | Propiedad | Modo | Descripción |
  | ------------- | ------------- | ------------- |
  | alpha | Escritura | Opacidad del componente, un valor entre 0 (0%) y 1 (100%) |
  | code | Lectura | Contiene el último código detectado |
  | content | Lectura | Contiene el contenido completo que ofrece el último código detectado |
  | backgroundColor | Escritura | Color de fondo del componente. Acepta un color de la tabla de colores (@color.primary) o un valor hexadecimal en formato #AARRGGBB o #RRGGBB |
  | format | Lectura | Indica el formato del último código detectado |
  | type | Lectura | Indica el tipo de contenido al que se refiere el último código detectado, pudiendo ser: `UNKNOWN`, `CONTACT_INFO`, `EMAIL`, `ISBN`, `PHONE`, `PRODUCT`, `SMS`, `TEXT`, `URL`, `WIFI`, `GEO`, `CALENDAR_EVENT` o `DRIVER_LICENSE`. |
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |
