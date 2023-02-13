# SendGrid
SendGrid is an email delivery service trusted by a lot of companies worldwide. You can use it to deliver emails to single users or massive email deliveries.
<br>
<br>

**More information:**
[https://sendgrid.com](https://sendgrid.com)
<br>
<br>
  
# Methods
<br>
<br>
  
## sendEmail
Sends a single email to a given email address. The body of the email can be plain text and/or html.
<br>
<br>
  
**Parameters:**  
| Key | Type | Description |
| ------------- | ------------- | ------------- |
| content_html | text | Email's body in html format. (opcional) |
| content_plain | text | Email's body in plain text format. (opcional) |
| from | text | Sender email address. It must have been previously configured on SendGrid. |
| to | text | Destination email address.|
| subject | text | Subject of the email |
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "sendgrid",
        "method": "sendEmail",
        "parameters":{
            "from": "sender@example.com",
            "to": "example@gmail.com",
            "subject": "Informe de ventas",
            "content_plain": "Hi! Remember to send me the sales report.",
            "content_html": "Hi!<br>Remember to send me the sales report."
        }
    }

<br>
<br>
  


## sendTemplate
Sends a single email to a given email address. The email will use a template designed on SendGrid and can be customized with user information passed in the parameters.
<br>
<br>
  
**Parameters:**  
| Key | Type | Description |
| ------------- | ------------- | ------------- |
| dynamic_template_data | objet | A JSON objet (key / value pairs) that contains the value for customizing the template. Each key should be written exactly as defined on the template. |
| from | text | Sender email address. It must have been previously configured on SendGrid. |
| template_id | text | ID of the template to be used, previously designed at SendGrid. |
| to | text | Destination email address. |
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "sendgrid",
        "method": "sendTemplate",
        "parameters":{
            "from": "sender@example.com",
            "template_id": "asdfghjkl",
            "to": "example@gmail.com",
            "dynamic_template_data": {
                "name": "John Smith",
                "expiration": "27/08/2023",
                "code": "ABCDE"
            }
        }
    }

<br>
<br>
  
