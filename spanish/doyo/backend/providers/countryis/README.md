# Country.is
Country.is es un API open-source muy sencilla que permite obtener el país a partir de una dirección IP. El país se devuelve en formato ISO.
<br>
<br>
**Más información:**
[https://country.is](https://country.is)
<br>
<br>
  
# Métodos
<br>
<br>
  
## user
Devuelve el país desde el que se está haciendo la llamada al API.
<br>
<br>
  
**Parámetros:**  
No requiere parámetros.
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "countryis",
        "method": "user"
    }

<br>
<br>
  


## fromIP
Devuelve el país al que pertenece la IP que se envía como parámetro.
<br>
<br>
**Parámetros:**  
| Clave  | Descripción |
| ------------- | ------------- |
| ip | Dirección IP de la que se quiere averiguar su país. |
<br>
<br>
  
**Ejemplo:**  
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
  
