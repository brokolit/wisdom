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
| back  | Vuelve a la vista anterior en el historial de navegación.|
| [delete](#function-delete) | Elimina contenido de un elemento. Por ejemplo, elimina un registro de una base de datos.|
| [divide](#function-divide) | Realiza una operación de división.|
| finish | Elimina la pantalla actual del historial de navegación.|
| [goto](#function-goto) | Navega a otra vista de la app. |
| [increase](#function-increase) | Realiza una operación de suma. |
| [login](#function-login) | Autentica a un usuario en el sistema de usuarios utilizado.|
| [logout](#function-logout) | Cierra la sesión del usuario actual. |
| [multiply](#function-multiply) | Realiza una operación de multiplicación.|
| [open](#function-open) | Abre una base de datos.|
| [play](#function-play) | Reproduce un archivo de audio. |
| [popup](#function-popup) | Muestra una ventana emergente.|
| [reduce](#function-reduce) | Realiza una operación de resta.|
| refresh | Vuelve a cargar la pantalla actual.|
| [signup](#function-signup) | Crea una cuenta de usuario en el sistema de usuarios utilizado.|
| [stop](#function-stop) | Detiene la reproducción de un archivo de audio.|
| [set](#function-set) | Establece un valor para una referencia.|



## Function ADD
bla bla bla


## Function DELETE
bla bla bla


## Function DIVIDE
bla bla bla


## Function GOTO
bla bla bla


## Function INCREASE
bla bla bla


## Function LOGIN
bla bla bla


## Function LOGOUT
bla bla bla


## Function MULTIPLY
bla bla bla


## Function OPEN
bla bla bla


## Function PLAY
bla bla bla


## Function POPUP
bla bla bla


## Function REDUCE
bla bla bla


## Function SIGNUP
bla bla bla


## Function STOP
bla bla bla


## Function SET
bla bla bla
