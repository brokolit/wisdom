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
  
## contacts.add
Añade o actualiza un contacto en Sendgrid. 
<br>
<br>
  
**Parámetros:**  
| Clave | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| email | text | Email del contacto. Éste es el único parámetro que es obligatorio, todos los demás son opcionales. |
| address_line_1 | text | Dirección (optional) |
| address_line_2 | text | Dirección, segunda línea (optional) |
| city | text | Ciudad (optional) |
| country | text | País (optional) |
| first_name | text | Nombre (optional) |
| last_name | text | Apellido (optional) |
| postal_code | text | Código postal (optional) |
| state_province_region | text | Estado, provincia o región (optional) |
| custom_fields | object | Un objeto que contiene los 'custom_fields'. Los custom fields deben haberse definido previamente en Sendgrid. (optional) |
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "sendgrid",
        "method": "contact.add",
        "parameters":{
            "email": "sender@example.com",
            "first_name": "Michael",
            "last_name": "Jordan",
            "custom_fields": {
                "team": "Chicago Bulls"
            }
        }
    }

<br>
<br>
  

## contacts.delete
Elimina un contacto de Sendgrid. Puedes utilizar el email o el id para identificar el contacto.
<br>
<br>
  
**Parámetros:**  
    
| Clave | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| email | text | Email del contacto que quieres eliminar (optional) |
| id | text | ID en Sendgrid del contacto que quieres eliminar (optional) |
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "sendgrid",
        "method": "contact.delete",
        "parameters":{
            "email": "sender@example.com"
        }
    }

<br>
<br>
  

## contacts.get
Obtiene toda la información de un contacto
<br>
<br>
  
**Parámetros:**  
| Clave | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| email | text | Email del contacto que quieres obtener (optional) |
| id | text | ID de Sendgrid del contacto que quieres obtener (optional) |
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "sendgrid",
        "method": "contact.get",
        "parameters":{
            "email": "sender@example.com"
        }
    }

<br>
<br>
  

## contacts.id
Get the ID of a contact from its email
<br>
<br>
  
**Parámetros:**  
| Clave | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| email | text | Email del contacto del que se quiere obtener el ID |
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "sendgrid",
        "method": "contact.id",
        "parameters":{
            "email": "sender@example.com"
        }
    }

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
  
