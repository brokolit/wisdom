# Open AI
Open AI is the techonology behind ChatGPT. It offers an artificial intelligence API that allows you to automatically generate text content from a given prompt.
<br>
<br>

**More information:**
[https://beta.openai.com](https://beta.openai.com)
<br>
<br>
  
# Methods
<br>
<br>
  
## createCompletion
Generates a text based on the parameters given.
<br>
<br>

**Parameters:**  

| Key  | Description |
| ------------- | ------------- |
| max_tokens | Indicates the maximum number of tokens to be consumed by the AI engine. The more tokens, the longer the answer will be. You should always thing that OpenAI bills based on the number of tokens consumed in each billing period. |
| model | Language model to be used. Depending on the chosen model, the answer will be more or less accurate, efficient and fast. You can use the models that you will find on OpenAI's documentation or the shortcuts provided by Doyo: `most-capable_davinci`, `capable_curie`, `cheap_babbage` o `cheapest_ada`. |
| prompt | Is the question you want to ask OpenAI. |
| temperature | A number between 0 and 1 that meassures the expected accuracy. A zero value means the maximum accuracy, while a higher number will provide more creative results. |
<br>
<br>
  
**Example:**  
<br>

    {
        "provider": "openai",
        "method": "createCompletion",
        "parameters": {
            "model": "most-capable_davinci",
            "prompt": "Dime un chiste donde salga una vaca y un perro",
            "max_tokens": 2000,
            "temperature": 0.3
        }
    }

<br>
<br>
  
