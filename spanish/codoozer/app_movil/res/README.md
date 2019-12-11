# Carpeta res

Esta carpeta debería ser incluida siempre, al menos para añadir un icono a la aplicación.

Dentro de esta carpeta se alojan todos los archivos que queramos utilizar de algún modo en nuestra aplicación. Los archivos que estén alojados directamente sobre la carpeta `res`, solo se añadirán a la app en caso de que se referencien desde algún punto de la app.

##### res / assets

Los archivos que se incluyan dentro de la subcarpeta `assets` se incluirán SIEMPRE en la app, aunque no se referencien directamente. Esto es útil, por ejemplo, si se piensa referenciar dichos recursos desde un campo de una base de datos, una cookie, etc.

##### res / fonts

Esta carpeta solo será necesaria si queremos incluir fuentes TTF dentro de nuestra app. Además de añadir los archivos en esta carpeta, será necesario dar de alta las fuente dentro del archivo app.json

##### res / icon

Esta carpeta debe incluir como mínimo un archivo PNG, que será el que se utilizará como icono por defecto para todos aquellos casos en los que no se especifique un icono concreto.

Si el nombre de un archivo es un número, por ejemplo `192.png`, se utilizará dicho archivo en aquellas plataformas o versiones que necesiten un icono con un ancho igual a dicho número.

También se puede añadir el prefijo `android` o `ios` para especificar que un icono es para una plataforma específica. Por ejemplo, `android.png`.

Incluso, se puede combinar el prefijo con un número. Por ejemplo, `android_192.png`.

