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
  | [monetization](#monetización) | Opcional | Contiene la configuración necesaria para activar la monetización por publicidad |
  | [purchases](#compras-inapp) | Opcional | Contiene la configuración necesaria para vender productos dentro de la app |
  | [colors](#colores) | Opcional | Contiene una tabla de colores, para poder referenciarlos desde partes de la app, con el objetivo de poder cambiar todo el aspecto de la app desde un mismo sitio. |
  | [database](#bases-de-datos) | Opcional | Contiene la lista de bases de datos, si las hubiere, que se van a utilizar en la app. |
  | [fonts](#tipografías-fonts) | Opcional | Contiene una tabla de fuentes TTF, en caso de que se quieran utilizar en la app.|



Si quieres ver un emplo de archivo app.json, [pincha aquí](app.json)




## Configuración Android
El parámetro `android` contiene algunas configuraciones necesarias para poder compilar la versión Android de la app.

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | package_name | Obligatorio | Nombre del paquete Android de la app. Debe ser un identificador único de la app, no pudiendo publicarse en los AppStores si ya existiera otro con el mismo nombre de paquete Android. |
  | version | Obligatorio | El número de versión que queremos compilar. Debe ser un número entero y deberíamos aumentar el valor cada vez que queramos actualizar la app en GooglePlay. |
  | version_name | Opcional | Es una cadena de texto que contiene tres números concatenados por puntos, indicando el número de versión, y subversión. De no introducirse, se cogerá el número de versión y se le añadirán dos ceros (1.0.0) |
  | maps_api_key | Opcional | Se deberá introducir en el caso de que queramos utilizar mapas de google dentro de la app. En este [enlace](https://developers.google.com/maps/documentation/android-sdk/get-api-key) se puede obtener información sobre cómo obtener el API key.|
  | firebase | Opcional | Se deberá introducir en el caso de que queramos utilizar algún producto de Firebase, como las notificaciones push, analytics, etc. El valor de este parámetro será un objeto JSON que definirá qué productos de Firebase se quiere utilizar. Más abajo se explican estos parámetros.|
  

La siguiente tabla muestra los parámetros que acepta el valor del parámetro `firebase`. Para activar un producto, basta con incluir la clave correspondiente y asignarle valor `true`:

  | Key  | Descripción |
  | ------------- | ------------- |
  | analytics | Firebase analytics |
  | authentication | Autenticación de usuarios de Firebase |
  | firestore | Base de datos firestore |
  | inapp-messaging | Mensajería in-app |
  | messaging | Notificaciones push |
  



## Configuración iOS

Información no disponible.



## Eventos de la app
El parámetro `events` contiene un objeto JSON que incluye la lista de eventos para los cuales queremos que la app reaccione.

Actualmente solo es posible definir el evento `onstart`, en el que se definirá el comportamiento de la app nada más abrirla. Normalmente este evento se utilizará para indicar la vista que hay que abrir en primer lugar.

Aquí se puede ver un ejemplo:

<pre>
    "events":{
        "onstart": {"function":"goto","view":"main"}
    },
</pre>

Más adelante se definirán otros eventos, como el `onexit`, `onpush`, etc.



## Monetización
El parámetro `monetization` especifica la configuración de la monetización. La siguiente tabla muestra la estructura del objeto JSON:


  | Key  ||||
  | ------------- | ------------- | ------------- | ------------- |
  | android | ads | networks | Array que contiene objetos, cada cual correspondiente a la configuración de una red publicitaria. |
  | android | ads | placements | Array que contiene objetos con información sobre los espacios de la app donde puede aparecer publicidad |

### Redes publicitarias (networks):

El parámetro `networks` tiene como valor un objeto JSON con la siguiente estructura:

  | Key  | Caracter | Valor |
  | ------------- | ------------- | ------------- |
  | admob | Opcional | Objeto JSON que contiene la configuración de la red publicitaria Admob | 

El parámetro Admob, tiene la siguiente estructura:

  | Key  | Valor |
  | ------------- | ------------- |
  | android_app_id | ID de la app asignado por Admob | 
  | android_test_devices | Una cadena de texto que contiene el token del dispositivo de testeo, o un array de cadenas si se quiere añadir varios dispositivos de testeo. |
  
  
### Emplazamientos (placements):

Cada objeto `placement` contiene información sobre un emplazamiento publicitario, pudiendo tener estos valores:

  | Key  | Valor |
  | ------------- | ------------- |
  | id | Nombre del emplazamiento, para referirse a él desde otras partes de la app. | 
  | network  | Red publicitaria usada por este emplazamiento. |
  | format  | Indica el tipo de anuncio. Puede ser `banner`, `interstitial` o `rewarded`. |
  | android_unit_id  | Es el ID de la unidad publicitaria ofrecido por la red para Android. |
  | ios_unit_id  | Es el ID de la unidad publicitaria ofrecido por la red para iOS. |

A continuación se muestra un ejemplo:
<pre>
    "monetization":{
        "ads":{
            "networks":{
                "admob":{
                    "android_app_id":"ca-app-pub-3940256099942544~3xxxxxxxx",
                    "android_test_devices": "26F2006560892_1D83871216xxxxxxxx"
                }
            },
            "placements":{
                "banner_menu":{
                    "network":"admob",
                    "format":"banner",
                    "android_unit_id":"ca-app-pub-4520545808487978/58xxxxxxxx"
                },
                "after_result":{
                    "network":"admob",
                    "format":"interstitial",
                    "android_unit_id":"ca-app-pub-4520545808487978/12xxxxxxxx"
                },
                "earn_questions":{
                    "network":"admob",
                    "format":"rewarded",
                    "android_unit_id":"ca-app-pub-4520545808487978/10xxxxxxxx"
                }
            }
        }
        
    }
</pre>


## Compras in-app
El parámetro `purchases` especifica la configuración de las ventas in-app. La siguiente tabla muestra la estructura del objeto JSON:


  | Key  | Caracter ||
  | ------------- | ------------- | ------------- |
  | googleplay | Opcional | Objeto JSON con la información para configurar las compras a través de GooglePlay |


### Compras vía GooglePlay
El parámetro `googleplay` del objeto `purchases` tiene la siguiente estructura JSON:

  | Key  | Descripción |
  | ------------- | ------------- |
  | products | Un array JSON que contiene la lista de productos a vender en la app |
  
  
Cada producto tiene a su vez la siguiente estructura JSON:

  | Key  | Descripción |
  | ------------- | ------------- |
  | id | Identificador del producto tal y como se ha definido en la consola de desarrollador de GooglePlay |
  | type | Indica el tipo de producto. Actualmente solo permite usar productos de tipo `eternal`, que son los que solo se necesita comprar una vez. |


  
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


## Bases de datos
El valor del parámetro `database` es un array JSON que contiene un objeto por cada base de datos que tenga la app.

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | id | Obligatorio | Identificador de la base de datos |
  | source | Obligatorio | Ruta al archivo que contiene la base de datos, relativa a la carpeta `res` o una URL |
  | type | Obligatorio | Tipo de base de datos. Puede ser uno de estos valores: `csv` |
  

## Tipografías (fonts)
El valor del parámetro `fonts` es un objeto JSON que contiene una lista de parámetros clave-valor, cada uno representando a una tipografía. La clave será el identificador que se quiera asignar a la tipografía, mediante el cual se hará referencia desde otras partes de la app, y el valor será el nombre del archivo que contiene la fuente, alojado en la subcarpeta `fonts`, que está dentro de `res`.

A continuación se puede ver un ejemplo:
<pre>
    "fonts":{
        "young":"fonts/Louis_George_Cafe.ttf",
        "renner":"fonts/Renner_ 400Book.ttf",
        "monospatial":"fonts/nk57-monospace-no-lt.ttf",
        "linux":"fonts/LinLibertine_R.ttf"
    }
</pre>
