# ¿Cómo crear una app móvil nativa con Codoozer?

Con un único módulo en nuestro proyecto podemos crear una app nativa universal, de modo que definiéndola una vez, genere versiones compatibles con distintas plataformas (Android Smartphone, Android Tablet, iPhone, iPad, etc.). Simplemente habría que introducir ciertas variaciones en el archivo app.json, para definir parámetros específicos de dichas plataformas.

Como alternativa, podríamos definir módulos específicos para cada plataforma, con el objetivo de crear interfaces distintas.

### Estructura de un proyecto de app móvil nativa

Para crear una app móvil nativa, nuestro proyecto debe contener la siguiente estructura

```

app.json
├── dialogs (opcional)    
├── external (opcional)
├── menus (opcional)
├── res 
    ├── assets (opcional)
    ├── fonts (opcional)
    └── icon
├── view_types
└── views

```


### app.json

Es el archivo JSON principal, que contiene la definición de los aspectos globales de la app, así como la configuración necesario para la generación de la app ejecutable.


### Carpeta dialogs

Esta carpeta solo es necesaria en caso de que queramos definir diálogos en nuestra app. Los diálogos son ventanas emergente que podemos utilizar para informar al usuario de algo o solicitarle algún tipo de información.


### Carpeta external

Esta carpeta solo es necesaria en caso de que queramos utilizar algún complemento ofrecido por un tercero. Por ejemplo, si vamos a utilizar Firebase de Google en nuestra app, deberíamos crear la carpeta `external` y poner dentro de ella el archivo `google-services.json`.


### Carpeta menus

Esta carpeta solo es necesaria si tenemos previsto incluir menús nativos dentro de nuestra app. Estos son los menús que se utilizan, por ejemplo, en las barras ActionBar, paneles laterales, componentes tipo `list`, etc.

En cambio, si lo que se pretende es que los menús de la app se compongan de componentes gráficos (imágenes, textos con enlaces, etc.), no será necesario crear esta carpeta.


### Carpeta res

Esta carpeta debería ser incluida siempre, al menos para añadir un icono a la aplicación.

Dentro de esta carpeta se alojan todos los archivos que queramos utilizar de algún modo en nuestra aplicación. Los archivos que estén alojados directamente sobre la carpeta `res`, solo se añadirán a la app en caso de que se referencien desde algún punto de la app.

#### res / assets

Los archivos que se incluyan dentro de la subcarpeta `assets` se incluirán SIEMPRE en la app, aunque no se referencien directamente. Esto es útil, por ejemplo, si se piensa referenciar dichos recursos desde un campo de una base de datos, una cookie, etc.
