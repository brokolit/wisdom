# Country.is
Country.is is an open-source API that allows you to obtaind the country from a given IP address. The country is return in ISO format.
<br>
<br>

**More information:**
[https://country.is](https://country.is)
<br>
<br>
  
# Methods
<br>
<br>
  
## user
Returns the contry based on the current IP of the user making the request.
<br>
<br>
  
**Parameters:**  
No parameters accepted.
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "countryis",
        "method": "user"
    }

<br>
<br>
  


## fromIP
Returns the contry based on the given IP passed as parameter.
<br>
<br>

**Parameters:**  
| Key  | Description |
| ------------- | ------------- |
| ip | IP address from which you want to find out the country. |
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "countryis",
        "method": "fromIP",
        "parameters": {
            "ip": "125.1.4.6"
        }
    }

<br>
<br>
  
