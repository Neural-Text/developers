# 🚀 Quick Start

### Get your API keys

Your API requests are authenticated using API keys. Any request that doesn't include an API key will return an error.

You can generate an API key from your Profile Settings page at any time.

**\<SCREEN>**

### Authentication

To authenticate, you must set a plain text header named `Authorization` with the contents of the header being `Token XXX` where `XXX` is your API Secret Key.

#### Example header

```
GET https://api.neuraltext.com/api/v1/projects/ HTTP/1.1
Authorization: Token Your.API.Key
```

## Make your first request

To make your first request, send an authenticated request to the projects endpoint. This will list all the projects you have access to.

{% swagger baseUrl="https://api.neuraltext.com/api/v1" method="get" path="/projects/" summary="List projects" expanded="true" %}
{% swagger-description %}
This endpoint will show the projects created or shared with you.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-response status="200" description="Success" %}
```javascript
{
  "next": null,
  "previous": null,
  "page": 1,
  "per_page": 10
  "count": 2,
  "results": [
    {
      "title": "Default Project",
      "id": "52073298-8060-4bda-b0c6-dfec88ae2cae",
      "owner": "your.account@neuraltext.com"
    },
    {
      "title": "Another Project",
      "id": "32985207-4bda-b0c6-8060-dfec88ae2cae",
      "owner": "your.account@neuraltext.com"
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="No project found" %}

{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using `curl` or `python`

{% tabs %}
{% tab title="cURL" %}
```bash
curl https://api.neuraltext.com/api/v1/projects \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}"
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
token_key = "Your.API.Key"

# See your project
url = "https://api.neuraltext.com/api/v1/projects/"
headers = {"Authorization": f"Token {token_key}"}

response = requests.get(url, headers=headers)
```
{% endtab %}
{% endtabs %}
