# SERP Analysis

### Tasks Ready

{% swagger method="get" path="/ready" baseUrl="https://api.neuraltext.com/api/v1/tasks" summary="Get ready tasks" %}
{% swagger-description %}
Price: **free**

Get the ready tasks created in the past 24 hours.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success response" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using `curl` or `python`

{% tabs %}
{% tab title="cURL" %}
```bash
curl https://api.neuraltext.com/api/v1/tasks/ready \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
token_key = "Your.API.Key"

# Get ready tasks in the last 24h
url = "https://api.neuraltext.com/api/v1/tasks/ready"
headers = {"Authorization": f"Token {token_key}"}

response = requests.get(url, headers=headers)
```
{% endtab %}
{% endtabs %}

### Create task

The task&#x20;

{% swagger method="post" path="/task/create" baseUrl="https://api.neuraltext.com/api/v1" summary="Start the analysis of SERP" %}
{% swagger-description %}
Price: **2 API units**

****
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="keywords" type="Array" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="location" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="language" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="engine" type="String" %}
`google-search`

 (default) or 

`google-news`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="webhook" type="String" %}

{% endswagger-parameter %}
{% endswagger %}

Take a look at how you might call this method using `curl` or `python`

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST https://api.neuraltext.com/api/v1/task/create \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}"
   -d '{"keywords":["how to optimize a blog", "how to write a blog"]}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
token_key = "Your.API.Key"

# Start the SERP Analysis
url = "https://api.neuraltext.com/api/v1/task/create"
data = {"keywords":["how to optimize a blog", "how to write a blog"]}
headers = {"Authorization": f"Token {token_key}"}

response = requests.post(url, json=data, headers=headers)
```
{% endtab %}
{% endtabs %}

### Task Detail

{% swagger method="get" path="/task/<id>" baseUrl="https://api.neuraltext.com/api/v1" summary="Get SERP data" %}
{% swagger-description %}
Price: 

**free**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" %}
`Token Your.API.Key`
{% endswagger-parameter %}
{% endswagger %}
