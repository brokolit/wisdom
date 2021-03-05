Las referencias son como direcciones virtuales donde se pueden almacenar datos y poder obtenerlos en el futuro para hacer uso de ellos. Las referencias pueden referirse a espacios de almacenamiento dentro de la propia aplicación (cookies, properties, bases de datos locales, componentes de la pantalla) o remotos (firebase, etc.). La elección del tipo de referencia a utilizar dependerá de cada caso.

Las referencias tienen mucha importancia a la hora de crear apps con Codoozer, pudiéndose utilizar como parámetros en las funciones, como origen de contenido en los elementos gráficos del interfaz, así como en otros lugares.

Gracias a las referencias, podremos dotar de mucha interactividad entre la app y el usuario.



## Cómo usar las referencias

Las referencias se pueden utilizar tanto para almacenar un dato en algún sitio como para recuperar un dato y utilizarlo.

Por ejemplo, si queremos recordar que un usuario ya ha entrado otras veces en la app.

Las referencias se pueden utilizar en diferentes sitios, como:

- Como parámetros de funciones.
- Como contenido de componentes (textos, imágenes, etc.).
- Como operadores en condiciones.

Para guardar un dato en una referencia, debemos utilizar la función SET. La misma acción sirve para editar el contenido en la referencia. También disponemos de otras funciones para alterar el contenido de una referencia: INCREASE, REDUCE, MULTIPLY y DIVIDE.

Para utilizar una referencia, hay que escribir el símbolo **"@"** seguido de la ruta a la referencia. Los pasos de la ruta se separan con un punto, siendo el primer paso el que indica el [tipo de referencia](tipos-de-referencia).

Las referencias se representan como cadenas de texto, con lo que se incluirán dentro de parámetros JSON que vayan entrecomillados. Si el valor del parámetro solo incluye la referencia, se escribirá tal cual. Por ejemplo:

<pre>
{
  "function":"set"
  "what":"@property.score",
  "value": 0
}
</pre>

También obtenerse el contenido de una referencia para utilizarlo de modo que personalice el valor de un parámetro u otra referencia. En ese caso, deberá incluirse la referencia secundaria entre paréntesis. Aquí unos ejemplos:

<pre>
{
  "function":"set"
  "what":"@property.fullName",
  "value": "(@property.name) (@property.lastName)"
}
</pre>


<pre>
{
  "function":"set"
  "what":"@firebase.firestore.users.(@property.currentUserID).city",
  "value": "Valencia"
}
</pre>



## Tipos de referencia

Los tipos de referencia que se pueden usar son:

| Tipo  | Descripción |
| ------------- | ------------- |
| [app](#referencia-app) | Permite acceder a cierta información de la app o el dispositivo.|
| assets | Permite acceder a los recursos guardados en la carpeta 'res/assets'.|
| [cookie](#cookies-y-properties) | Las cookies permiten almacenar datos de forma permanente, de modo que estarán disponibles la próxima vez que se abra la app.|
| database | Las referencias a las bases de datos permiten leer y escribir en bases de datos. |
| disk | Se usa cuando se quiere guardar información en un archivo ubicado en la memoria externa, accesible desde fuera de la app. |
| element | Las referencias a los componentes permiten obtener y establecer las propiedades de éstos. |
| firebase | Permite acceder a los componentes de Firebase. |
| [property](#cookies-y-properties) | Las properties permiten almacenar datos de forma volátil, que se borrarán al salir de la app. 	|
| wrapper | Permite obtener y establecer propiedades del wrapper. |



## Referencia APP

Las referencias @app permiten obtener a información sobre la app o el dispositivo.

Se detallan en la siguiente tabla:

| Nombre  | Descripción |
| ------------- | ------------- |
| @app.admob_device_id | Devuelve el ID de dispositivo usado por Admob. Puede servir para poder configurar nuestro dispositivo como dispositivo de pruebas, para mostrar anuncios ficticios. |
| @app.gaid | Obtiene el Google Advertising ID, que es un código único que identifica al dispositivo, aunque puede ser reseteado por el usuario.|
| @app.lang | Obtiene el idioma por defecto del dispositivo. |
| @app.lang.iso | Obtiene el idioma por defecto del dispositivo en formato ISO sin la región. |
| @app.lang.iso3 | Obtiene el idioma por defecto del dispositivo en formato ISO3. |
| @app.lang.region | Obtiene el idioma por defecto del dispositivo en formato ISO incluyendo la región. |
| @app.location | Obtiene la ubicación GPS actual del dispositivo, en formato "latitud,longitud". Debe usarse solo cuando haya una 'view' cargada. |
| @app.location.latitude | Obtiene la latitud de la ubicación GPS actual del dispositivo. Debe usarse solo cuando haya una 'view' cargada. |
| @app.location.longitude | Obtiene la longitud de la ubicación GPS actual del dispositivo. Debe usarse solo cuando haya una 'view' cargada. |
| @app.time | Obtiene la fecha y hora actual del dispositivo. El formato depende de la configuración local del dispositivo. |
| @app.timestamp | Obtiene el timestamp actual a partir de la fecha y hora actual en el dispositivo. Es el número de milésimas de segundo entre la fecha actual y el 1 de Enero de 1970. Puede ser útil, por ejemplo, para medir el tiempo que ha transcurrido entre dos instantes distintos. |
| @app.version | Obtiene la versión actual de la app. |


## Cookies y properties

Ambos tipos de referencias permiten guardar y recuperar valores. La diferencia es que los valores almacenados en las referencias de tipo @cookie se siguen guardando aunque se cierre la aplicación, mientras que en las de tipo @property, el valor se desecha cuando la aplicación se cierra.

El desarrollador es libre de escoger el nombre de cada referencia, que no debe contener espacios ni símbolos especiales, solo letras (a-z, A-Z), números o el guión bajo.

<pre>
@property.username
</pre>

<pre>
@cookie.username
</pre>

A la hora de recuperar el valor almacenado en la referencia, se pueden añadir modificadores a continuación del nombre, separando por punto cada modificador. Los modificadores permiten alterar el valor obtenido, aunque el valor almacenado en la referencia no varía. Se pueden encadenar varios modificadores. En tal caso, cada modificador modificará el valor obtenido en la modificación previa. Por ejemplo, si queremos obtener el valor guardado en la cookie 'price', dividido por 2 y sumándole 5, usaríamos:

<pre>
@cookie.price./2.+5
</pre>

La siguiente tabla muestra los posibles modificadores para valores de tipo texto:

| Modificador  | Descripción |
| ------------- | ------------- |
| entero | Devuelve el caracter que ocupa la posición `entero`. |
| inicio-final | Permite obtener la subcadena de texto comprendida entre los caracteres que ocupan la posición `inicio` y `final`. Ambos valores deben ser números enteros positivos. Si el valor `final` es superior a la longitud del texto, se obtendrá la subcadena hasta el último caracter del texto. |
| json | Si el texto almacenado está en formato JSON, nos permitiría acceder a los valores de éste, considerando que a continuación del modificador escribiríamos la ruta del valor que queremos obtener dentro del json.|
| length | Devuelve la longitud de un texto. |
| lower | Convierte un texto a letras minúsculas. |
| md5 | Devuelve el hash md5 generado a partir de un texto. |
| trim | Elimina, si los hubiere, los espacios al principio y al final de un texto. |
| upper | Convierte un texto a letras mayúsculas. |
| urldecode | Decodifica un texto que esté en formato urlencode para obtener el texto original. |
| urlencode | Codifica el texto en formato urlencode para poder usarse como parámetros dentro de una URL. |


La siguiente tabla muestra los posibles modificadores para valores de tipo numérico:

| Modificador  | Descripción |
| ------------- | ------------- |
| text | Convierte el número a texto. Puede ser útil para evitar almacenar números en formato científico (1e12). |
| +N | Suma N al valor original o previamente modificado. |
| -N | Resta N al valor original o previamente modificado. |
| *N | Multiplica el valor original o previamente modificado por N. |
| /N | Divide el valor original o previamente modificado por N. |
| %N | Devuelve el resto de dividir el valor original o previamente modificado por N. |
| N% | Devuelve el porcentaje especificado por N sobre el valor original o previamente modificado. |
| ^N | Devuelve el valor original o previamente modificado elevado a la N-ésima potencia.  |
| dN | Redondea el valor original o previamente modificado usando N posiciones decimales. |
| abs | Devuelve el valor absoluto del valor original o previamente modificado. |
| acos | Devuelve el arcocoseno en grados del valor original o previamente modificado. |
| asin | Devuelve el arcoseno en grados del valor original o previamente modificado. |
| atan | Devuelve la arcotangente en grados del valor original o previamente modificado. |
| cos | Devuelve el coseno del valor original o previamente modificado (en grados). |
| sin | Devuelve el seno del valor original o previamente modificado (en grados). |
| tan | Devuelve la tangente del valor original o previamente modificado (en grados). |
| sqrt | Devuelve la raíz cuadrada del valor original o previamente modificado. |

En caso de que los modificadores que especifican un número N, y que dicho número incluya decimales (con un punto), deberá usarse entre paréntesis, para evitar que el punto se pueda interpretar como el final del modificador. Por ejemplo:

<pre>
@cookie.price.*(1.21)
</pre>
