# Write

The capabilities of LLMs can be immense: for instance, you can use it to come up with new concepts or variations of existing content. This could range from narrative ideas to business models, character profiles to advertising taglines.&#x20;

This example will show you how to employ the API to generate ideas on how machine learning can improve education:

```
Generate some ideas combining machine learning and education:
```

{% swagger method="post" path="/write/" baseUrl="https://api.neuraltext.com/api/v1/ai" summary="Complete the provided prompt" expanded="false" %}
{% swagger-description %}
Price: 

**1 API unit every 200 tokens in input/output**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="text" required="true" type="String" %}
A prompt
{% endswagger-parameter %}

{% swagger-parameter in="body" name="temperature" type="Float" %}
The creativity of the model.

\


A float number ranging from 

`0`

 to 

`1`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="max_tokens" type="Integer" %}
Lenght of the text you want to generated, ranging from `1` to `3000`

Default is `100`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```json
{
    "status": "ok",
    "text": "1. Automated grading systems that utilize machine learning to quickly and accurately grade student assignments.\n2. Adaptive learning systems that use machine learning algorithms to tailor educational content to individual students.\n3. Using machine learning to detect early warning signs of academic problems and intervene with personalized support."
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid payload" %}
```javascript
{
    "error": "temperature must be a float number between 0 and 1.",
}
```
{% endswagger-response %}

{% swagger-response status="429: Too Many Requests" description="Rate limit reached" %}
The rate limit for this endpoint is 10 calls per second. If you exceed it, you will get this error.

```javascript
{
    "error": "It seems you are generating text too fast. Please try again in a few moments."
}
```
{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using `curl` or `python`

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.neuraltext.com/api/v1/ai/write/ \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}" \
   -d '{"text":"A prompt", "temperature":0.9, "max_tokens":100}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
token_key = "Your.API.Key"

# Write
url = "https://api.neuraltext.com/api/v1/ai/write/"
data = {"text":"A prompt", "temperature":0.9, "max_tokens":100}
headers = {"Authorization": f"Token {token_key}"}

response = requests.post(url, json=data, headers=headers)
```
{% endtab %}
{% endtabs %}
