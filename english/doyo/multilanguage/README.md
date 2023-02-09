# Multilanguage (i18n)

Doyo is able to generate multilanguage software.

In order to achieve that, all the JSON values that contain a text that corresponds to some label that will be displayed on the app, will accept either a single text string or a JSON object that will contain key/value pairs for each translation of the text. Each translation key will be the ISO code for the corresponding language.

In case of different languages, one of them must use the key `default` instead of an ISO code, so that the application will use that translation whenever the device language is not included as a translated language in the app.

Here's an example of using a single language::

`"name":"Hello world"`

This other example shows the same text using multilanguage:

<pre>
"name":{
  "default":"Hello world",
  "es":"Hola mundo"
}
</pre>
