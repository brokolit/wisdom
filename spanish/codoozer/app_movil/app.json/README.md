# app.json

Es el archivo JSON principal, que contiene la definición de los aspectos globales de la app, así como la configuración necesario para la generación de la app ejecutable.

Este archivo debe alojarse en el directorio raíz del proyecto.

La siguiente tabla muestra los parámetros que puede contener:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | id | Obligatorio | Identificador único asignado por Codoozer |
  | project_name | Obligatorio | Nombre identificativo del proyecto, asignado por el desarrollador |
  | name | Obligatorio | Nombre de la app, tal cual aparecerá al instalarse en un dispositivo. Acepta [multilenguaje](../../multilenguaje) |
  | [android](#configuración-android) | Opcional | Contiene configuración específica para generar la versión compatible con dispositivos Android. Por tanto, solo es necesario en caso de que se desee generar dicha versión. |
  | [ios](#configuración-ios) | Opcional | Contiene configuración específica para generar la versión compatible con dispositivos iOS (Apple). Por tanto, solo es necesario en caso de que se desee generar dicha versión. |
  | [events](#eventos-de-la-app) | Obligatorio | Define el comportamiento de la app como respuesta a determinados eventos. Debe contener, como mínimo, el evento `onstart`, en el que definiremos qué debe hacer la app al ejecutarse. Por ejemplo, la función `goto` para cargar una vista. |
  | [colors](#colores) | Opcional | Contiene una tabla de colores, para poder referenciarlos desde partes de la app, con el objetivo de poder cambiar todo el aspecto de la app desde un mismo sitio. |
  | [fonts](#tipografías-fonts) | Opcional | Contiene una tabla de fuentes TTF, en caso de que se quieran utilizar en la app.|



## Configuración Android


## Configuración iOS

Información no disponible.


## Eventos de la app


## Colores
El valor del parámetro `colors` es un objeto JSON que contiene una lista de parámetros clave-valor, cada uno representando a un color. La clave será el identificador que se quiera asignar al color, mediante el cual se hará referencia desde otras partes de la app, y el valor será el código hexadecimal del color, precedido por almohadilla (#), y en formato #RRGGBB o #AARRGGBB.

A continuación se puede ver un ejemplo:
<pre>
    "colors":{
        "colorPrimary":"#00c2a9",
        "colorPrimaryDark": "#00a58c",
        "colorPrimaryLight": "#b7f0e7",
        "colorAccent": "#f15a9e",
        "colorSecondary": "#ffde39",
        "colorSecondaryDark": "#fec632",
        "colorSecondaryLight": "#fbe98d",
        "blue": "#0cafe8",
        "headlines": "#d7d4e3",
        "grey":"#999999",
        "titles": "#01579b",
        "fbutton": "#01579b",
        "white": "#ffffff",
        "black": "#000000"
    }
</pre>

## Tipografías (fonts)
