# app.json

Es el archivo JSON principal, que contiene la definición de los aspectos globales de la app, así como la configuración necesario para la generación de la app ejecutable.

Este archivo debe alojarse en el directorio raíz del proyecto.

La siguiente tabla muestra los parámetros que puede contener:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | id | Obligatorio | Identificador único asignado por Codoozer |
  | project_name | Obligatorio | Nombre identificativo del proyecto, asignado por el desarrollador |
  | name | Obligatorio | Nombre de la app, tal cual aparecerá al instalarse en un dispositivo. Acepta [multilenguaje](../../multilenguaje) |
  | android | Opcional | Contiene configuración específica para generar la versión compatible con dispositivos Android. Por tanto, solo es necesario en caso de que se desee generar dicha versión. |
  | ios | Opcional | Contiene configuración específica para generar la versión compatible con dispositivos iOS (Apple). Por tanto, solo es necesario en caso de que se desee generar dicha versión. |
  | events | Obligatorio | Define el comportamiento de la app como respuesta a determinados eventos. Debe contener, como mínimo, el evento `onstart`, en el que definiremos qué debe hacer la app al ejecutarse. Por ejemplo, la función `goto` para cargar una vista. |
  | colors | Opcional | Contiene una tabla de colores, para poder referenciarlos desde partes de la app, con el objetivo de poder cambiar todo el aspecto de la app desde un mismo sitio. |
  | fonts | Opcional | Contiene una tabla de fuentes TTF, en caso de que se quieran utilizar en la app.|
