# Doppio
Doppio permite generar un documento PDF a partir del contenido de una página web.
<br>
<br>

**Más información:**
[https://doppio.sh](https://doppio.sh)
<br>
<br>
  
# Métodos
<br>
<br>
  
## pdf.sync
Genera un documento PDF a partir del contenido de la URL dada. El API responde con la URL de descarga del documento PDF una vez éste se haya generado.
<br>
<br>
  
**Parámetros:**  
  
| Clave  | Descripción |
| ------------- | ------------- |
| url | URL de la página que se quiere convertir a pdf |
<br>
<br>
  
**Ejemplo:**  
<br>

    {
        "provider": "doppio",
        "method": "pdf.sync",
         "parameters": {
            "url": "https://doyo.tech"
        }
    }

<br>
<br>