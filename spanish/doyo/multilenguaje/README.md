# Multilenguaje (i18n)

Doyo está preparado para genera software multilenguaje.

En aquellos parámetros JSON cuyo valor es un texto que corresponde a una etiqueta que se mostrará en el interfaz de la aplicación, se podrá introducir bien un texto único o un objeto JSON que contenga pares clave valor para cada idioma deseado, siendo la clave el código ISO de dicho idioma.

En caso de querer usar más de un idioma, uno de ellos debería usar la clave `default` en lugar de su código ISO, para que el software sepa cuáles son los textos a mostrar en caso de que el idioma del usuario final no sea uno de los definidos en la app.

Aquí se puede ver un ejemplo de idioma único:

`"name":"Mi app genial"`

Y en este otro ejemplo, podemos ver el mismo texto con multilenguaje:

<pre>
"name":{
  "default":"My cool app",
  "es":"Mi app genial"
}
</pre>
