# Funciones

Las funciones son las acciones que queremos que la app realice, como repuesta a un evento (se inicia la app, el usuario toca algo en la pantalla, se va a cargar una pantalla nueva, se ha cargado la pantalla actual, etc.).

Una función se define como un objeto JSON, que debe tener obligatoriamente el parámetro `function`, que define el tipo de acción que queremos que se realice.

En este fragmento se muestra la definición mínima de un objeto `function`:
<pre>
{
	"function":"goto"
}
</pre>

Las funciones se pueden invocar individualmente o como una secuencia, mediante un array de objetos, de modo que se ejecutarán una después de la otra:

<pre>
[
	{
		"function":"play"
	},
	{
		"function":"goto"
	}
]
</pre>


Dentro de cada objeto función, dependiendo del tipo de función que estemos definiendo, podrá haber otros parámetros que complementen la definición de la función.


Veamos primero los diferentes tipos de funciones, enumerados en esta tabla:


| Tipo  | Descripción |
| ------------- | ------------- |
| abort | Detiene la ejecución de la cadena de funciones en la que está incluída.|
| [add](#function-add) | Añade contenido a un elemento. Por ejemplo, un registro a una base de datos. |
| back | Vuelve a la vista anterior en el historial de navegación.|
| [browser](#function-browser) | Abre el navegador web externo y carga una URL.|
| [calculate](#function-calculate) | Permite realizar cálculos sobre una base de datos.|
| [delete](#function-delete) | Elimina contenido de un elemento. Por ejemplo, elimina un registro de una base de datos.|
| [divide](#function-divide) | Realiza una operación de división.|
| [file](#function-file) | Permite al usuario seleccionar uno o más archivos. |
| finish | Elimina la pantalla actual del historial de navegación.|
| [goto](#function-goto) | Navega a otra vista de la app. |
| [increase](#function-increase) | Realiza una operación de suma. |
| [interstitial](#function-interstitial) | Muestra un anuncio a pantalla completa. |
| [login](#function-login) | Autentica a un usuario en el sistema de usuarios utilizado.|
| [logout](#function-logout) | Cierra la sesión del usuario actual. |
| [multiply](#function-multiply) | Realiza una operación de multiplicación.|
| [open](#function-open) | Abre una base de datos.|
| [play](#function-play) | Reproduce un archivo de audio. |
| [popup](#function-popup) | Muestra una ventana emergente.|
| [purchase](#function-purchase) | Inicia el flujo para realizar una compra in-app.|
| [reduce](#function-reduce) | Realiza una operación de resta.|
| refresh | Vuelve a cargar la pantalla actual.|
| [reward](#function-reward) | Lanza un anuncio de vídeo recompensado.|
| [round](#function-round) | Redondea un número.|
| [signup](#function-signup) | Crea una cuenta de usuario en el sistema de usuarios utilizado.|
| [stop](#function-stop) | Detiene la reproducción de un archivo de audio.|
| [set](#function-set) | Establece un valor para una referencia.|
| [track](#function-track) | Registra un evento en la herramienta de analytics.|



## Function ADD
Añade contenido a un elemento. Por ejemplo, un registro a una base de datos.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Contiene un objeto JSON con uno o varios parámetros clave-valor, que es lo que queremos añadir.|
| to | Referencia al elemento al que queremos añadir el contenido.|

Ejemplo:
<pre>
{
	"function":"add",
	"what":
		{
			"name":"John",
			"age":23
		}
	"to":"@firebase.firestore.students"
}
</pre>


## Function BROWSER
Abre el navegador web del dispositivo y carga en él una URL.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| url | URL que queremos cargar en el navegador.|

Ejemplo:
<pre>
{
	"function":"browser",
	"url":"https://codoozer.com"
}
</pre>

## Function CALCULATE
Permite realizar cálculos sobre una base de datos. Por ejemplo, para calcular la suma de todos los registros, el promedio, las distancias a algún punto, etc.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| collection | Referencia a la colección sobre la que se quiere realizar el cálcula.|
| field | Campo de la colección a usar para realizar el cálculo.|
| into | Referencia donde se ha de guardar el resultado en caso de ser un único valor.|
| operation | Operación a realizar.|
| parameter | Un parámetro opcional necesario para algunos tipos de operaciones.|

El campo operation puede aceptar estos valores:

| Parámetro  | Descripción |
| ------------- | ------------- |
| average | Calcula el promedio de todos los valores de la colección del campo definido por el parámetro `field`.|
| distance | Si el campo definido por `field` contiene coordenadas GPS, devuelve la distancia de la ruta definida por todos los puntos de la colección.|
| distanceTo | Si el campo definido por `field` contiene coordenadas GPS, calcula la distancia entre cada punto y el definido por el parámetro `parameter`, guardando cada resultado en el mismo registro, en el campo definido por el parámetro `into`.|
| length | Calcula el número de registros en la colección.|
| max | Devuelve el ID del registro que contiene el valor máximo entre todos los valores del campo definido por el parámetro `field` en la colección.|
| max_value | Calcula el valor máximo entre todos los valores del campo definido por el parámetro `field` en la colección.|
| min | Devuelve el ID del registro que contiene el valor mínimo entre todos los valores del campo definido por el parámetro `field` en la colección.|
| min_value | Calcula el valor mínimo entre todos los valores del campo definido por el parámetro `field` en la colección.|
| sum | Calcula la suma de todos los valores de la colección del campo definido por el parámetro `field`.|





Ejemplo:
<pre>
{
	"function": "calculate",
	"collection": "@database.locations",
	"field": "gps",
	"into": "distance",
	"operation": "distanceTo",
	"parameter": "@app.location",
}
</pre>


## Function DELETE
Elimina contenido de un elemento. Por ejemplo, elimina un registro de una base de datos.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia al contenido que queremos eliminar.|

Ejemplo:
<pre>
{
	"function":"delete",
	"what":"@firebase.firestore.students.(@property.selectedStudent)"
}
</pre>

## Function DIVIDE
Realiza una operación de división.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia cuyo valor lo queremos dividir por una cantidad.|
| by | Cantidad por la que queremos dividir.|

Ejemplo:
<pre>
{
	"function":"divide",
	"what":"@property.score",
	"by":2
}
</pre>

## Function FILE
Permite al usuario seleccionar uno o más archivos.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| into | Referencia donde se guardará la ruta al archivos seleccionado o, en caso de elegir más de un archivo, la referencia debe ser una ruta a una base de datos o firestore.|
| multiple | Para indicar si se quiere permitir seleccionar varios archivos. Si no se añade este parámetro, solo se permite seleccionar un archivo.|
| onfailed | Función/es a ejecutar en caso de que el usuario no escoja ningún archivo.|
| onsuccess | Función/es a ejecutar en caso de que el usuario seleccione archivos correctamente.|
| type | Tipo MIME para poder restringir la selección a un determinado tipo de archivo. Por ejemplo 'image/*' permitirá seleccionar solo imágenes, 'image/png' solo archivos PNG, etc. (más información en (#https://developer.mozilla.org/es/docs/Web/HTTP/Basics_of_HTTP/MIME_types) |

Ejemplo:
<pre>
{
	"function":"file",
	"into":"@property.tempFile",
	"multiple": false,
	"onsuccess":[
		{
			"function":"goto",
			"view":"profile"
		}
	]
}
</pre>

Al seleccionar archivos, éstos se copian al almacenamiento interno de la app, guardándose la ruta en la referenca especificada en `into` se almacenar´, que luego podrá ser utilizada como `value` en funciones `set`, por ejemplo.

En caso de selección múltiple, todos los archivos se copian al almacenamiento local, pero la referencia `into` no almacenará la ruta a un archivo, sino un documento json con la siguiente estructura:

<pre>
{
	"length":3,  // número de archivos
	"files":[
		{
			"value":"ruta al archivo 1"
		},
		{
			"value":"ruta al archivo 2"
		},
		{
			"value":"ruta al archivo 3"
		}
	]
}
</pre>

Ejemplo:
<pre>
{
	"function":"file",
	"into":"@database.userdata.photos",
	"multiple": true,
	"onsuccess":[
		{
			"function":"goto",
			"view":"profile"
		}
	]
}
</pre>


## Function GOTO
Navega a otra vista de la app.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| view | ID de la vista a la que queremos navegar.|

Ejemplo:
<pre>
{
	"function":"goto",
	"view":"main_menu"
}
</pre>


## Function INCREASE
Realiza una operación de suma.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia a cuyo valor le queremos sumar una cantidad.|
| by | Cantidad que queremos sumar.|

Ejemplo:
<pre>
{
	"function":"increase",
	"what":"@property.score",
	"by":5
}
</pre>


## Function INTERSTITIAL
Muestra un anuncio de tipo intersticial a pantalla completa. Consulta la sección de monetización para obtener ayuda sobre cómo configurar las redes de anuncios. El anuncio intersticial se muestra como una transición entre dos pantallas (vistas). En cuanto a flujo de la app, funcionaría como la función GOTO, pero mostrando un anuncio antes de cargar la vista de destino.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| placement | ID del emplazamiento de anuncios.|
| view | Vista a la que se tiene que ir cuando se cierre el anuncio o cuando no haya anuncio disponible.|

Ejemplo:
<pre>
{
	"function":"interstitial",
	"placement":"after_game",
	"view":"menu"
}
</pre>


## Function LOGIN
Autentica a un usuario en el sistema de usuarios utilizado.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| provider | Proveedor de autenticación. Actualmente solo se acepta "firebase".|
| email | Email del usuario.|
| pass | Contraseña introducida por el usuario.|
| onvalid | Contiene una función (o una secuencia de funciones) que se ejecutará si la validación del usuario es correcta.|
| oninvalid | Contiene una función (o una secuencia de funciones) que se ejecutará si la validación del usuario es incorrecta.|

Ejemplo:
<pre>
{
	"function":"login",
	"provider":"firebase",
	"email":"@property.email",
	"pass":"@property.pass",
	"onvalid":{
		"function":"goto",
		"view":"main"
	},
	"oninvalid":{
		"function":"popup",
		"dialog":"login_error"
	}
}
</pre>


## Function LOGOUT
Cierra la sesión del usuario actual.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| provider | Proveedor de autenticación. Actualmente solo se acepta "firebase".|

Ejemplo:
<pre>
{
	"function":"logout",
	"provider":"firebase"
}
</pre>


## Function MULTIPLY
Realiza una operación de multiplicación.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia a la base de datos.|

Ejemplo:
<pre>
{
	"function":"open",
	"what":"@database.restaurants"
}
</pre>


## Function OPEN
Abre una base de datos.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia cuyo valor lo queremos multiplicar por una cantidad.|
| by | Cantidad por la que queremos multiplicar.|

Ejemplo:
<pre>
{
	"function":"multiply",
	"what":"@property.score",
	"by":2
}
</pre>


## Function PLAY
Reproduce un archivo de audio.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia al archivo de audio que queremos reproducir. Puede ser el nombre de un archivo contenido en la carpeta `res`.|
| loop (opcional) | Si existe y es `true`, el audio se reproduce a modo de loop.

Ejemplo:
<pre>
{
	"function":"play",
	"dialog":"song.mp3"
}
</pre>


## Function POPUP
Muestra una ventana emergente.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| dialog | ID del diálogo que queremos mostrar|

Ejemplo:
<pre>
{
	"function":"popup",
	"dialog":"should_accept_policy"
}
</pre>


## Function PURCHASE
Inicia el flujo para realizar una compra in-app.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| product | ID del producto que se quiere vender.|
| onowned | Función/es a ejecutar en caso de que el usuario ya haya comprado previamente el producto.|
| onerror | Función/es a ejecutar en caso de que se produzca algún error en la transacción o el usuario lo cancele.|
| onsuccess | Función/es a ejecutar en caso de que la compra se realice correctamente.|

Ejemplo:
<pre>
{
	"function":"purchase",
	"product":"full_version",
	"onsuccess":{
		"function":"popup",
		"dialog":"purchase_ok"
	},
	"onowned":{
		"function":"popup",
		"dialog":"product_already_owned"
	},
	"onerror":{
		"function":"popup",
		"dialog":"try_again"
	}
}
</pre>


## Function REDUCE
Realiza una operación de resta.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia a cuyo valor le queremos restar una cantidad.|
| by | Cantidad a restar.|

Ejemplo:
<pre>
{
	"function":"reduce",
	"what":"@firebase.firestore.users.(@firebase.user.id).kids.(@property.selectedKid).score",
	"by":10
}
</pre>


## Function REWARD
Lanza un anuncio de vídeo recompensado.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| placement | ID del emplazamiento de anuncio.|
| source | Identificador de la variable donde se debe guardar la recompensa recibida.|
| onreward | Función/es a ejecutar en caso de que el usuario obtenga la recompensa correctamente.|
| ondismiss | Función/es a ejecutar en caso de que el usuario cierre el anuncio antes de ganar la recompensa.|
| onnotready | Función/es a ejecutar en caso de que no haya ningún anuncio disponible.|

Ejemplo:
<pre>
{
	"function":"reward",
	"placement":"earn_gold",
	"source":"@property.currentReward",
	"onreward":{
		"function":"popup",
		"dialog":"gotreward"
	},
	"ondismiss":{
		"function":"popup",
		"dialog":"try_again"
	},
	"onnotready":{
		"function":"popup",
		"dialog":"ad_not_ready"
	}
}
</pre>


## Function ROUND
Redondea un número.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia cuyo valor queremos redondear.|
| decimals | Número de decimales a los que queremos redondear.|

Ejemplo:
<pre>
{
	"function":"round",
	"what":"@property.score",
	"decimals":2
}
</pre>


## Function SIGNUP
Crea una cuenta de usuario en el sistema de usuarios utilizado.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| provider | Proveedor de autenticación. Actualmente solo se acepta "firebase".|
| email | Email del usuario.|
| pass | Contraseña introducida por el usuario.|
| onvalid | Contiene una función (o una secuencia de funciones) que se ejecutará si el creación de la cuenta es exitosa.|
| oninvalid | Contiene una función (o una secuencia de funciones) que se ejecutará si la creación de la cuenta fracasa.|
| onexists | Contiene una función (o una secuencia de funciones) que se ejecutará si el usuario ya existe en el sistema.|
| onweakpassword | Contiene una función (o una secuencia de funciones) que se ejecutará si se detecta que la contraseña es muy débil y, por tanto, no es válida.|

Ejemplo:
<pre>
{
	"function":"signup",
	"provider":"firebase",
	"email":"@property.email",
	"pass":"@property.pass",
	"onvalid":{
		"function":"goto",
		"view":"main"
	},
	"oninvalid":{
		"function":"popup",
		"dialog":"signup_error"
	},
	"onexists":{
		"function":"popup",
		"dialog":"user_exists"
	},
	"onweakpassword":{
		"function":"popup",
		"dialog":"weak_password"
	}
}
</pre>


## Function STOP
Detiene la reproducción de un archivo de audio.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia al audio cuya reproducción hay que detener. Si el valor es "all", se detienen todos los audios que se estén reproduciendo.|

Ejemplo:
<pre>
{
	"function":"stop",
	"what":"song.mp3"
}
</pre>


## Function SET
Establece un valor para una referencia.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| what | Referencia a la que queremos establecer un valor.|
| value | Valor que queremos asignar.|

Ejemplo:
<pre>
{
	"function":"set",
	"what":"@property.city",
	"value":"Valencia"
}
</pre>


## Function TRACK
Registra un evento en la herramienta de Analytics.

Estos son sus parámetros:

| Tipo  | Descripción |
| ------------- | ------------- |
| name | Nombre del evento.|
| params | Objeto JSON con los parámetros del evento.|

Ejemplo:
<pre>
{
	"function":"track",
	"name":"exam_complete",
	"params":{
		"result":10,
		"examID":123
	}
}
</pre>
