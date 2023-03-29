# Firebase Messaging
Firebase Messaging is the tool offered by Firebase that allows sending push notifications to users of applications.
<br>
<br>

**More information:**
[https://firebase.com](https://firebase.com)
<br>
<br>
  
# Methods
<br>
<br>
  
## messaging.send
Sending a push notification to one or multiple recipients. The recipients are identified through their 'FCM token'.

For apps created with Doyo, a user's token can be obtained by using the reference '@firebase.fcm.token'.
<br>
<br>
  
**Parameters:**  
| Key | Type | Description |
| ------------- | ------------- | ------------- |
| to | text | The FCM token of the recipient. |
| topic | text | Send a message to all the users subscribed to a topic. |
| title | text | Title of the message (optional) |
| body | text | Content of the message (optional)|
| data | object | Data to send through the push message (optional) |
<br>
<br>
  
**Examples:**  
<br>

    {
        "provider": "firebase",
        "method": "messaging.send",
        "parameters":{
            "to": "fWfsSrOCRCGtlux0hP57gw:APA91b....",
            "title": "Welcome!",
            "body": "Get your promo code today"
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
            "title": "Welcome!",
            "body": "Get your promo code today"
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
