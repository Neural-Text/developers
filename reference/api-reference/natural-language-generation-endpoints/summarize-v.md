# Summarize (β)

{% hint style="warning" %}
This endpoint is currently only available for custom integrations. [**Contact us**](mailto:humans@neuraltext.com)****
{% endhint %}

{% swagger method="post" path="/summarize/" baseUrl="https://api.neuraltext.com/api/v1/ai" summary="Summarize a text" %}
{% swagger-description %}
Price: 

**1 API unit every 200 tokens in input**
{% endswagger-description %}

{% swagger-parameter in="body" name="text" required="true" %}
The text you want to summarize
{% endswagger-parameter %}

{% swagger-parameter in="body" name="sentences" type="Integer" %}
Number of the sentences the summary will have (up to `10`).

Default to `5` .


{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid data in payload" %}
If you don't specify `text` in the payload, you will get this message:

```javascript
{
    "error": "Text is required"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Account not enabled" %}
```javascript
{
    "error": "Your account is not enabled to perform this action, please contact us."
}
```
{% endswagger-response %}

{% swagger-response status="422: Unprocessable Entity" description="Insufficient API units" %}
```javascript
{
    "error": "Insufficient API units"
}
```
{% endswagger-response %}

{% swagger-response status="503: Service Unavailable" description="Model currently not available" %}
```javascript
{
    "error": "Summary LLM not available"
}
```
{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using `curl` or `python`

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.neuraltext.com/api/v1/ai/summarize/ \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}" \
   -d '{"text":"The text you want to summarize", "sentences":3}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
token_key = "Your.API.Key"

# Summarize
url = "https://api.neuraltext.com/api/v1/ai/summarize/"
data = {"text":"The text you want to summarize", "sentences":3}
headers = {"Authorization": f"Token {token_key}"}

response = requests.post(url, json=data, headers=headers)
```
{% endtab %}
{% endtabs %}
