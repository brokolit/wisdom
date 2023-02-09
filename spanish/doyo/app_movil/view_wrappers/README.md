# Contenedores de vistas (view_wrappers)

Los contenedores de vista, como su nombre indica, son los distintos entornos de la app donde se añadirán las vistas.

En una app, podemos tener diferentes apartados o entornos, cada uno con diferentes componentes (action bar, tabs, paginación, etc.).

Cada contenedor de vistas se define en un archivo JSON independiente, alojado en la carpeta `view_wrappers`.

En esta tabla se muestran los parámetros que puede tener:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | id | Obligatorio | Identificador único |
  | [actionbar](#actionbar) | Opcional | Hay que añadirlo si se quiere que el view_wrapper tenga un ActionBar. El valor es un objeto JSON que define las propiedades de dicha barra |
  | [drawer](#drawer) | Opcional | Hay que añadirlo si se quiere que el view_wrapper tenga un panel lateral deslizante. El valor es un objeto JSON que define las propiedades de dicho panel. |
  | [pager](#pager) | Opcional | Hay que añadirlo si se quiere que el view_wrapper tenga un paginardor, pudiendo albergar varias vistas. El valor es una array que contiene los IDs de las vistas que se quieren incluir. |
  
Si no se añade ningún componente, el contenedor de vistas será un entorno a pantalla completa.

  
  
## ActionBar
Un ActionBar es una barra superior que se muestra en la pantalla y puede contener, además de un título, botones de acción.
  
  | Key  | Descripción |
  | ------------- | ------------- |
  | back_button | Indica si la barra debe mostrar un botón de volver a la izquierda del título |
  | background_color | Indica el color de fondo de la barra. Puede ser un valor absoluto, en formato #RGB o #ARGB, o una referencia a un color predefinido |
  | color | Indica el color del título y de los botones |
  | title | Título a mostrar en la barra. Acepta multilenguaje |
  | menu | Es el ID del menú definido en la carpeta `menus` que queremos añadir a la barra. Las opciones del menú se pueden mostrar como iconos de acción o aparecer dentro de un menú emergente, en función de como se defina en el JSON del menú correspondiente. |
  | ios_type | Este parámetro solo se utiliza en las apps de iOS. Indica el tipo de barra, si es comprimida (`inline`) o grande (`large`)  |
  
Mediante la función `SET` se pueden modificar estas propiedades del actionbar:
  
   | Propiedad | Descripción |
  | ------------- | ------------- |
  | @wrapper.actionbar.title | Permite cambiar el título del actionbar |

    
  
## Drawer
Un Drawer es un panel lateral que aparece al hacer swipe desde el borde lateral de la pantalla del dispositivo o al pulsar en el botón correspondiente en un ActionBar.
  
  | Key  | Descripción |
  | ------------- | ------------- |
  | icon | Nombre del archivo que contiene el icono |
  | title | Título a mostrar en la cabecera del panel. Acepta multilenguaje |
  | subtitle | Subtítulo a mostrar en la cabecera del panel. Acepta multilenguaje |
  | menu | ID del menú a utilizar |
  
Mediante la función `SET` se pueden modificar estas propiedades del drawer:
  
   | Propiedad | Descripción |
  | ------------- | ------------- |
  | @wrapper.drawer.icon | Permite cambiar la imagen del icono en la cabecera del drawer. Debe ser el nombre de un archivo incluído en la carpeta `assets` o una referencia que guarde una imagen |
  | @wrapper.drawer.title | Permite cambiar el texto del título de la cabecera del drawer. |
  | @wrapper.drawer.subtitle | Permite cambiar el texto del subtítulo de la cabecera del drawer. |
  
  ## Pager
Un Pager (paginador) se utiliza para cargar varias `view` y poder navegar entre ellas mediante scroll horizontal. 
  
  | Key  | Descripción |
  | ------------- | ------------- |
  | tabs | Indica si hay que incluir las pestañas de navegación para cambiar de una vista a otra. Puede ser `true` o `false`. De no existir el parámetro, se considera valor `false`. |
  | views | Contiene la lista de vistas que debe content el paginador. Es un array de cadenas de texto, cada cual es el ID de una vista. |
  
  
  
  

