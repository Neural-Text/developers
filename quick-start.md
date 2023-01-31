# 🚀 Quick Start

### Get your API keys

Your API requests are authenticated using API keys. Any request that doesn't include an API key will return an error.

### Authentication

To authenticate, you must set a plain text header named `Authorization` with the contents of the header being `Token XXX` where `XXX` is your API Secret Key.

#### Example header

```
GET https://api.neuraltext.com/api/v1/balance/ HTTP/1.1
Authorization: Token Your.API.Key
```

## Make your first request

To make your first request, send an authenticated request to the API units balance endpoint. This will show the API units available on your account.

{% swagger method="get" path="/balance/" baseUrl="https://api.neuraltext.com/api/v1" summary="Get the available API units on your account" expanded="true" %}
{% swagger-description %}
Price: 

**free**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    "api_units": 20000,
}
```
{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using `curl` or `python`

{% tabs %}
{% tab title="cURL" %}
```bash
curl https://api.neuraltext.com/api/v1/balance/ \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
token_key = "Your.API.Key"

# Get API Units balance
url = "https://api.neuraltext.com/api/v1/balance/"
headers = {"Authorization": f"Token {token_key}"}

response = requests.get(url, headers=headers)
```
{% endtab %}
{% endtabs %}
