# Open AI
Open AI es la tecnología que hay detrás de ChatGPT. Ofrece un API de inteligencia artificial para generación de texto de forma automática.
<br>
<br>
**Más información:**
[https://beta.openai.com](https://beta.openai.com)
<br>
<br>
  
# Métodos
<br>
<br>
  
## createCompletion
Genera un texto de forma automática cumpliendo los criterios que se indican en los parámetros.
<br>
<br>
**Parámetros:**  
| Clave  | Descripción |
| ------------- | ------------- |
| max_tokens | Indica el número de tokens máximo a consumir por el motor de IA. A mayor número de tokens, la respuesta será más larga. Hay que tener en cuenta que el API de OpenAI factura por tokens consumidos. |
| model | Modelo de lenguaje a utiliza. En función del modelo, la respuesta será más o menos precisa, eficiente y rápida. Se pueden usar los modelos que se encuentran en la documentación de OpenAI o las abreviaciones de Doyo: `most-capable_davinci`, `capable_curie`, `cheap_babbage` o `cheapest_ada`. |
| prompt | Es la pregunta que se le hace a OpenAI y de la que se espera respuesta. |
| temperature | Un número entre 0 y 1 que mide la precisión esperada. Un valor de cero será la máxima precisión, mientras que un valor más alto generará resultados más creativos. |
<br>
<br>
**Ejemplo:**  
<br>

    {
        "provider": "doyo",
        "method": "timestamp",
        "parameters": {
            "model": "most-capable_davinci",
            "prompt": "Dime un chiste donde salga una vaca y un perro",
            "max_tokens": 2000,
            "temperature": 0.3
        }
    }

<br>
<br>
  
