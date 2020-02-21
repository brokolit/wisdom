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

Para guardar un dato en una referencia, debemos utilizar la función SET. La misma acción sirve para editar el contenido en la referencia. También disponemos de otras funciones para alterar el contenido de una referencia: INCREASE, REDUCE, MULTIPLY y DIVICE.

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
| cookie | Las cookies permiten almacenar datos de forma permanente, de modo que estarán disponibles la próxima vez que se abra la app.|
| property | Las properties permiten almacenar datos de forma volátil, que se borrarán al salir de la app. |
| element | Las referencias a los componentes permiten obtener y establecer las propiedades de éstos. |
| database | Las referencias a las bases de datos permiten leer y escribir en bases de datos. |
| firebase | Permite acceder a los componente sde Firebase. |
