# SendGrid
SendGrid es el servicio de envío de emails en el que confían muchas empresas para enviar correos a escala. Se puede usar para enviar emails individuales a usuarios concretos o para envío masivo de emails.
<br>
<br>
**Más información:**
[https://sendgrid.com](https://sendgrid.com)
<br>
<br>
  
# Métodos
<br>
<br>
  
## sendEmail
Envía un email a una dirección de correo. El contenido del email se especifica en los parámetros.
<br>
<br>
  
**Parámetros:**  
| Clave  | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| content_html | texto | Cuerpo del mensaje en formato html. (opcional) |
| content_plain | texto | Cuerpo del mensaje en formato texto plano. (opcional) |
| from | texto | Dirección de correo desde la que se enviará el email. Debe haberse dado de alta previamente como `sender`en SendGrid. |
| to | texto | Dirección de correo del destinatario. |
| subject | texto | Asunto del email |
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "sendgrid",
        "method": "sendEmail",
        "parameters":{
            "from": "sender@example.com",
            "to": "example@gmail.com",
            "subject": "Informe de ventas",
            "content_plain": "Hola! Recuerda enviarme el informe pronto",
            "content_html": "Hola!<br>Recuerda enviarme el informe pronto"
        }
    }

<br>
<br>
  


## sendTemplate
Envía un email a una dirección de correo. Dicho email utiliza un template predefinido previamente en SendGrid y que se puede personalizar mediante los parámetros enviados en la llamada.
<br>
<br>
  
**Parámetros:**  
| Clave  | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| dynamic_template_data | objeto | Objeto json (clave / valor) que contiene los valores para personalizar el template. Cada clave debe escribirse de forma idéntica a como se haya definido en el template. |
| from | texto | Dirección de correo desde la que se enviará el email. Debe haberse dado de alta previamente como `sender`en SendGrid. |
| template_id | texto | Identificador del template a utilizar, que ha sido diseñado previamente en SendGrid. |
| to | texto | Dirección de correo del destinatario. |
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "sendgrid",
        "method": "sendTemplate",
        "parameters":{
            "from": "sender@example.com",
            "template_id": "asdfghjkl",
            "to": "example@gmail.com",
            "dynamic_template_data": {
                "name": "Ramón Bilbao",
                "expiracion": "27/08/2023",
                "codigo": "ABCDE"
            }
        }
    }

<br>
<br>
  
