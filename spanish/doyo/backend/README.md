# ¿Qué es un backend?
  
El término `backend`se refiere a un software que se ejecuta en un servidor para gestionar información y/o realizar funciones que no se pueden realizar desde una app o una web, también llamados `frontend`. Con Doyo es muy sencillo construir un `backend` sin necesidad de programar.
  
Existen dos formas de construir un backend con Doyo:
  
- [Uso del API Doyo](#doyo_api)
- [Desarrollo nocode de funciones](#desarrollo_de_funciones)
  
    
## Doyo API
  
Doyo proporciona funciones propias de backend, así como integraciones con APIs de terceros, que son muy fáciles de acceder, tanto desde proyectos de tipo `app` como de tipo `web`.
  
Para poder hacer uso de la API de Doyo, simplemente hay que activarla en el proyecto en el que se quiera usar. Para ello, hay que ir a Configuración > Integraciones. Una vez dentro, simplemente hay que activar las herramientas que se quieren utilizar. En el caso de algunas APIs externas, el usuario deberá tener una cuenta con el proveedor correspondiente y vincularla en Doyo, normalmente a través de un `api key` o similar que dicho proveedor facilitará.
  
También es posible hacer uso de la API de Doyo desde apps y webs que no hayan sido creadas con Doyo, [como se explica más adelante](#como_usar_el_backend_desde_mi_proyecto_creado_fuera_de_doyo)
  
  
## Desarrollo de funciones
  
Disponible próximamente
  
  
## Cómo usar el backend desde mi proyecto creado con Doyo
  
En proyectos creados con Doyo, se podrá acceder al `backend` mediante el uso de la función `api`.
  
En aquellos métodos del API que no necesiten parámetros, también se podrá obtener su respuesta mediante el uso de la referencia @api, componiendo la ruta con el nombre del `provider` seguido del método, separando la ruta con puntos.
  
  
## Cómo usar el backend desde mi proyecto creado fuera de Doyo
  
Si nuestra app o web no han sido creados con Doyo y solo queremos crear con Doyo el backend, deberemos crear un proyecto de tipo `backend` en Doyo.
  
Para acceder al `backend` se realizará una llamada de tipo POST a la siguiente dirección:
```
https://api.doyo.tech
```
  
En la configuración del proyecto se obtendrá un `api key`. Deberemos añadir la siguiente cabecera en la llamada:
```
Authorization: "Bearer [api key del proyecto]"
```
  
Y el cuerpo de la llamada, en formato JSON, deberá contener al menos los siguientes parámetros:
  
 | Parámetro | Descripción |
  | ------------- | ------------- |
  | provider | Identificador del proveedor a utilizar |
  | method | Función a utilizar de entre las ofrecidas por el provider |