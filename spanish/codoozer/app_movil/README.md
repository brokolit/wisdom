# ¿Cómo crear una app móvil nativa con Codoozer?

Con un único módulo en nuestro proyecto podemos crear una app nativa universal, de modo que definiéndola una vez, genere versiones compatibles con distintas plataformas (Android Smartphone, Android Tablet, iPhone, iPad, etc.). Simplemente habría que introducir ciertas variaciones en el archivo app.json, para definir parámetros específicos de dichas plataformas.

Como alternativa, podríamos definir módulos específicos para cada plataforma, con el objetivo de crear interfaces distintas.

### Estructura de un proyecto de app móvil nativa

Para crear una app móvil nativa, nuestro proyecto debe contener la siguiente estructura

[app.json](app.json)  
├── [dialogs (opcional)](dialogs)  
├── [external (opcional)](external)  
├── [menus (opcional)](menus)  
├── [res](res)  
│&emsp;&emsp;├── [assets (opcional)](res)  
│&emsp;&emsp;├── [fonts (opcional)](res)  
│&emsp;&emsp;└── [icon](res)  
├── [view_types](view_types)  
└── [views](views)  


### Funciones

Las funciones son las acciones que queremos que la app realice, como repuesta a un evento (se inicia la app, el usuario toca algo en la pantalla, se va a cargar una pantalla nueva, se ha cargado la pantalla actual, etc.).

Para más información, accede a la página de [funciones](functiones).


### Referencias

Las referencias se usan para acceder a algún objeto (cookies, variables, bases de datos, elementos del interfaz, etc.) y así obtener o establecer su valor.

Las referencias tienen mucha importancia a la hora de crear apps con Codoozer, pudiéndose utilizar como parámetros en las funciones, como origen de contenido en los elementos gráficos del interfaz, así como en otros lugares.

Para más información, accede a la página de [referencias](referencias).

Gracias a las referencias, podremos dotar de mucha interactividad entre la app y el usuario.


