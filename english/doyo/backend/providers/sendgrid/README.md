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

## contacts.add
Adds/updates a contact on Sendgrid. 
<br>
<br>
  
**Parameters:**  
| Key | Type | Description |
| ------------- | ------------- | ------------- |
| email | text | Email of the contact. This is the only parameter you need to create a contact. All other parameters are optionsl. |
| address_line_1 | text | Address (optional) |
| address_line_2 | text | Address, second line (optional) |
| city | text | City (optional) |
| country | text | Country (optional) |
| first_name | text | First name (optional) |
| last_name | text | Last name (optional) |
| postal_code | text | Postal code (optional) |
| state_province_region | text | State, province or region (optional) |
| custom_fields | object | An object containing custom fields. Those custom fields must be previously configured on Sendgrid. (optional) |
<br>
<br>
  
**Example:**  
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
Delete a contact from Sendgrid. You can use the email or the id to identify the contact.
<br>
<br>
  
**Parameters:**  
| Key | Type | Description |
| ------------- | ------------- | ------------- |
| email | text | Email of the contact you want to delete (optional) |
| id | text | Sendgrid's ID of the contact you want to delete (optional) |
<br>
<br>
  
**Example:**  
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
Get all the information from a contact
<br>
<br>
  
**Parameters:**  
| Key | Type | Description |
| ------------- | ------------- | ------------- |
| email | text | Email of the contact you want to get (optional) |
| id | text | Sendgrid's ID of the contact you want to get (optional) |
<br>
<br>
  
**Example:**  
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
  
**Parameters:**  
| Key | Type | Description |
| ------------- | ------------- | ------------- |
| email | text | Email of the contact you want to get its ID |
<br>
<br>
  
**Example:**  
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
  
