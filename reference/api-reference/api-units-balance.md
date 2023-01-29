# API units balance

### Check API units balance <a href="#check-api-units-balance" id="check-api-units-balance"></a>

Make sure that you have a sufficient number of API units:

* within the [Usage info tab](https://app.neuraltext.com/account/usage)
* or via API request (it’s free)

### What if I don't have enough API units <a href="#what-if-i-dont-have-enough-api-units_" id="what-if-i-dont-have-enough-api-units_"></a>

When you don't have enough credit to perform an action, you will get an error with status code `422`.

{% swagger method="get" path="/balance" baseUrl="https://api.neuraltext.com/api/v1" summary="Get the available API units on your account" expanded="true" %}
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
curl https://api.neuraltext.com/api/v1/balance \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
token_key = "Your.API.Key"

# Get API Units balance
url = "https://api.neuraltext.com/api/v1/balance"
headers = {"Authorization": f"Token {token_key}"}

response = requests.get(url, headers=headers)
```
{% endtab %}
{% endtabs %}

