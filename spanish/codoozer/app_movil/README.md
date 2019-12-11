# ¿Cómo crear una app móvil nativa con Codoozer?

Con un único módulo en nuestro proyecto podemos crear una app nativa universal, de modo que definiéndola una vez, genere versiones compatibles con distintas plataformas (Android Smartphone, Android Tablet, iPhone, iPad, etc.). Simplemente habría que introducir ciertas variaciones en el archivo app.json, para definir parámetros específicos de dichas plataformas.

Como alternativa, podríamos definir módulos específicos para cada plataforma, con el objetivo de crear interfaces distintas.

### Estructura de un proyecto de app móvil nativa

Para crear una app móvil nativa, nuestro proyecto debe contener la siguiente estructura

```
app.json
├── dialogs        # Contiene la definición de las ventanas pop-up
├── external       # Contiene la definición de las ventanas pop-up
├── menus          # Contiene la definición de las ventanas pop-up
├── res            # Contiene la definición de las ventanas pop-up
├── view_types     # Contiene la definición de las ventanas pop-up
└── views          # Contiene la definición de las ventanas pop-up
```
