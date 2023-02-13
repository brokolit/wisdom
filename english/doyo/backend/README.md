# What is a backend?
  
A `backend` is a piece software that runs on a server in order to manage information and/or perform functions that can't (or shouldn't) be performed from an app or a website (both called `frontend`). With Doyo it is quite easy to build a `backend` without programming.
  
There are two ways to build a backend with Doyo:
  
- [Use the API Doyo](#doyo-api)
- [Build nocode backend functions](#build-nocode-backend-functions)
  
    
## Doyo API
  
Doyo provides its own ready-to-user backend functions, some of which connect with 3rd party APIs, which are very easy to use from your project, no matter if it's a web or an app project.

In order to use the API Doyo, just activate it in the project your want to use it. Go to Settings>Integrations. Once inside, just activate those tools you plan to use. For using some 3rd party APIs, you must open an account on those 3rd party tools and link it on Doyo, normally using an `api key` or similar provided by that tool.

It's also possible to use API Doyo from apps or websites that are not built with Doyo, as [explained below](#how-to-use-the-backend-from-a-project-not-built-with-doyo)
  
<br>
<br>
<br>  
  
## Build nocode backend functions
  
Soon available
  
  
## How to use the backend from my project built with Doyo
  
In projects built with Doyo, the `backend` can be used by using the function `api`.
  
There are some methods that don't accept parameters. Those can be accessed from the reference @api, forming the route with the name of the `provider`, followed be the method's identifier and using dots to separate every step of it.
  
  
## How to use the backend from a project not built with Doyo
  
If your app or website has been built outside Doyo and you just want Doyo for building your backend, you must create a project of type o `backend` on Doyo.

For accessing the `backend` from your project, just make a POST request to the address:
  
```
https://api.doyo.tech
```
  
In your project settings you'll find the `api key`. You must add that key in the Authorization header of that request, as a bearer token:
```
Authorization: "Bearer [your_project_api_key]"
```
  
The body of the request must be en JSON format and include at least these parameters:
  
 | Parámetro | Descripción |
  | ------------- | ------------- |
  | provider | Identificador del proveedor a utilizar |
  | method | Función a utilizar de entre las ofrecidas por el provider |
  | parameters | Optional. A JSON object with the parameters you want to pass to the method |