# Firebase Messaging
Firebase Messaging es la herramienta ofrecida por Firebase que permite realizar envíos de notificaciones push a los usuarios de aplicaciones.
<br>
<br>

**Más información:**
[https://firebase.com](https://firebase.com)
<br>
<br>
  
# Métodos
<br>
<br>
  
## messaging.send
Envío de una notificación push a uno o a múltiples destinatarios. Los destinatarios se identifican a través de su 'token FCM'.

Para apps creadas con Doyo, el token de un usuario se puede obtener mediante el uso de la referencia '@firebase.fcm.token'.
<br>
<br>
  
**Parámetros:**  
| Clave | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| to | text | Token FCM del destinatario al que queremos enviar el mensaje. |
| topic | text | Nombre de un topic, se enviará el mensaje a todos los usuarios suscritos a dicho topic. |
| title | text | Título del mensaje (optional) |
| body | text | Contenido del mensaje (optional) |
| data | object | Datos a enviar a través del mensaje push (optional) |
<br>
<br>
  
**Ejemplos:**  
<br>

    {
        "provider": "firebase",
        "method": "messaging.send",
        "parameters":{
            "to": "fWfsSrOCRCGtlux0hP57gw:APA91b....",
            "title": "Bienvenido!",
            "body": "Consigue tu bono de descuento"
        }
    }

<br>
<br>
  
<br>

    {
        "provider": "firebase",
        "method": "messaging.send",
        "parameters":{
            "to": [
                "fWfsSrOCRCGtlux0hP57gw:APA91b....",
                "my9Vs0KRl8JfHe5xbF5HuN5wMrmkM..."
            ]
            "title": "Bienvenido!",
            "body": "Consigue tu bono de descuento"
        }
    }

<br>
<br>

    {
        "provider": "firebase",
        "method": "messaging.send",
        "parameters":{
            "to": [
                "fWfsSrOCRCGtlux0hP57gw:APA91b....",
                "my9Vs0KRl8JfHe5xbF5HuN5wMrmkM..."
            ]
            "data": {
                "credits": 10
            }
        }
    }

<br>
<br>

