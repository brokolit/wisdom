# Doyo
Doyo ofrece una serie de funciones básicas que normalmente es mejor que se ejecuten en un servidor. Por ejemplo, si queremos obtener la fecha actual, no conviene fiarse de la fecha configurada en el dispositivo donde se ejecuta una app, sino utilizar la fecha real que se puede obtener en el servidor.
<br>
<br>
  
# Métodos
<br>
<br>
  
## timestamp
Devuelve el timestamp del servidor, que es el número de segundos transcurridos desde el 1 de Enero de 1970.
<br>
**Parámetros:**  
No requiere parámetros.
<br>
<br>
**Ejemplo:**<br>
<textarea>
{
    "provider": "doyo",
    "method": "timestamp"
}
</textarea>
<br>
<br>
  
## timestamp.format
Devuelve la fecha actual del servidor con el formato especificado.
<br>
**Parámetros:**<br>
<br>
| key  | Descripción |
| ------------- | ------------- |
| format | Formato en el que se quiere obtener la fecha, basado en SimpleDateFormat |
<br>
<br>
  
## timestamp.milliseconds
Devuelve el timestamp del servidor, pero medido en milésimas de segundo
<br>
**Parámetros:**
No requiere parámetros.
<br>
<br>
  