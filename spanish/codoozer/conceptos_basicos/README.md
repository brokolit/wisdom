# ¿Cómo se estructura un proyecto?

Los proyectos en Codoozer se componen de lo siguiente:

- Archivos JSON
- Carpetas
- Recursos

### Archivos JSON

Los archivos JSON, son archivos de texto plano que contienen información estructurada. En Codoozer se utilizan para definir toda la aplicación: maquetación de las pantallas, comportamiento, opciones, etc.

Un proyecto contiene distintos archivos JSON, utilizados para distintos propósitos (pantallas, menús, diálogos, etc.).


### Carpetas

Las carpetas ayudan a organizar los distintos archivos JSON, así como otros recursos.

La carpeta raíz solo contendrá un archivo JSON principal, app.json, que contiene información general de la aplicación. Además, contendrá una serie de carpetas específicas que contendrán el resto de archivos JSON y recursos de la app. Estas carpetas deben seguir una nomenclatura concreta, que podrá variar en función del tipo de proyecto que estemos creando (app móvil, web, backend script, etc.)

### Recursos

Además de los archivos JSON, un proyecto contendrá archivos de recursos, que son el contenido de la app (imágenes, audios, vídeos, etc.).




Estructura en función del proyecto
=============

Para aprender más sobre la estructura del proyecto, elige uno de los tipos de proyecto:

[App móvil nativa](https://github.com/brokolit/wisdom/tree/master/spanish/codoozer/app_movil)
