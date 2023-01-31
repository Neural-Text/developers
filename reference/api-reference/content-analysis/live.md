# Live

Live endpoint provides real-time data on top 10 search engine results for the specified keyword along with the content analysis for each result.

This endpoint will return data in a single HTTP request.

**Turnaround time:** up to 20 seconds

{% swagger method="post" path="/serp/" baseUrl="https://api.neuraltext.com/api/v1/live" summary="Get live Google Search and analyze results" %}
{% swagger-description %}
Price: **1 API Unit**

Analyze top 10 results ranking for a query in real-time Google Search.

Returns a list of `topics` found in the SERP and a list of `results`

Each result will have:

`title`\
`description`\
`url`\
`rank`\
`domain`\
`headers`\
`wordcount`\
`text`
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
`Token Your.API.Key`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="keyword" required="true" %}
The keyword you want to get results for, up to 700 characters. 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="country" required="true" %}
2-letters country code.

Default `us`.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="language" required="true" %}
2-letters language code.

Default `en`.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success response" %}
```javascript
{"results": [
  {
     "title" : "The title of the page",
     "description": "Page description",
     "url": "https://example.com",
     "rank": 1,
     "domain": example.com
     "headers": 
     "wordcount": 200,
     "text" : "The text of this page in a string"
   }
...
],
 "topics": [
    "Topic 1",
    "Topic 2",
    ...
 ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Missing data in payload" %}
```javascript
{
 "error": "Missing data in payload. This endpoint requires a keyword, a country (2-digit country code) and a language (2-digit language code)."
}
```
{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using `curl` or `python`

{% tabs %}
{% tab title="cURL" %}
{% code overflow="wrap" %}
```bash
curl -X POST https://api.neuraltext.com/api/v1/live/serp/ \
   -H "Accept: application/json" \
   -H "Authorization: Token {Your.API.Key}" \
   -d '{"keyword":"how to optimize a blog", "country": "us", "language": "en"}'
```
{% endcode %}
{% endtab %}

{% tab title="Python" %}
{% code overflow="wrap" %}
```python
import requests
token_key = "Your.API.Key"

# Start the SERP Analysis
url = "https://api.neuraltext.com/api/v1/task/create"
data = {"keyword":"how to optimize a blog", "country": "us", "language": "en"}
headers = {"Authorization": f"Token {token_key}"}

response = requests.post(url, json=data, headers=headers)
```
{% endcode %}
{% endtab %}
{% endtabs %}

###
