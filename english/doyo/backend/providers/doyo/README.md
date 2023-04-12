# Doyo
Doyo offers a set of basic functions that should be normally be perform on the backend side and not on the frontend. For example, if we need to get the current time, it is more reliable to trust the server time setting than the time set in the end users's device.
<br>
<br>
  
# Methods
<br>
<br>
  
## random.pin
Generates a random numeric PIN with a given number of digits.
<br>
<br>
    
**Parameters:**  
<br>
| key  | Descripción |
| ------------- | ------------- |
| digits | Number of digits that the PIN code must have. |
<br>
<br>
  
  
## timestamp
Returns the time on the server, as the number of seconds since January 1st, 1970.
<br>
<br>

**Parameters:**  
No parameters accepted.
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "doyo",
        "method": "timestamp"
    }

<br>
<br>
  
## timestamp.format
Returns the time on the server in the given format.
<br>
<br>
  
**Parameters:**  
<br>
| Key  | Description |
| ------------- | ------------- |
| format | The format you want the date to be shown, based on SimpleDateFormat |
<br>
<br>
  
## timestamp.milliseconds
Returns the time on the server, as the number of milliseconds since January 1st, 1970.
<br>
<br>
  
**Parameters:**  
No parameters accepted.
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "doyo",
        "method": "timestamp.milliseconds"
    }
    
<br>
<br>
  
## uuid
Returns a universial unique identifier (UUID).
<br>
<br>
  
**Parameters:**  
No parameters accepted.
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "doyo",
        "method": "uuid"
    }
    
<br>
<br>
  